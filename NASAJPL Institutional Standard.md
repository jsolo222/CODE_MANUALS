NASA/JPL Institutional Coding Standard for the C Programming Language
JPL DOCID D-60411
Laboratory for Reliable Software (LaRS)
Jet Propulsion Laboratory
California Institute of Technology

INTRODUCTION
This document describes the JPL institutional coding standard for the C programming language. The standard is designed to support the development of safety-critical and mission-critical software. It is meant to complement, not replace, existing international coding standards for C, such as MISRA-C (2004).
The main focus is on code that is used in spacecraft flight software, instrument flight software, and mission-critical ground support software. The rules aim to prevent the introduction of defects that could remain undetected in the code until the software is in operational use.
The standard is based on 10 rules that can be enforced by strong static source code analyzers. Strict enforcement means that all identified violations are true violations (i.e., there are few or no false positives), and no serious defects can remain undetected (i.e., there are few or no false negatives).
The Price of Defects:
Finding and fixing a defect costs less than one hour of labor during initial coding, ten to fifteen hours during formal testing, one hundred or more hours if found in operational use, and cannot be fixed at all if the software is already deployed in space.
Philosophy:
The ten rules are meant to be minimally intrusive. They require only local, not global, analysis of the code to verify compliance. This means they can be checked efficiently and thoroughly by automated tools.

RULE 1: AVOID COMPLEX FLOW CONSTRUCTS
Restrict all code to very simple control flow constructs. Do not use goto statements, setjmp or longjmp constructs, or direct or indirect recursion.
Rationale:
Simpler control flow translates into stronger capabilities for verification and often results in improved code clarity. The banishment of recursion is perhaps the most surprising part of the rule. Note, however, that recursion is problematic in embedded code for two reasons: it can lead to uncontrolled stack growth, and it makes worst-case execution time analysis extremely difficult.
Banishment of goto and setjmp/longjmp is more obvious: these constructs defeat most static analysis tools and reduce code clarity. In flight code, we cannot accept code that we cannot thoroughly analyze statically.

RULE 2: GIVE ALL LOOPS A FIXED UPPER-BOUND
All loops must have a fixed upper-bound. It must be trivially possible for a checking tool to prove statically that a preset upper-bound on the number of iterations of a loop cannot be exceeded. If the loop-bound cannot be proven statically, the rule is considered violated.
Rationale:
The absence of recursion and the presence of loop bounds prevents runaway code. This rule is essential for proving termination. Note that the rule does not require that the loop bound be small (though in practice, it often should be). The rule does require that it is easily provable that the loop cannot exceed a preset bound.
c#define MAX_SAMPLES 1000

int samples = 0;
while (samples < MAX_SAMPLES && sensor_data_available()) {
    process_sample();
    samples++;
}

RULE 3: DO NOT USE DYNAMIC MEMORY ALLOCATION AFTER INITIALIZATION
Do not use dynamic memory allocation after task initialization.
Rationale:
This rule is common for safety-critical software and appears in most coding guidelines. The reason is simple: memory allocators, such as malloc, and garbage collectors often have unpredictable behavior that can significantly impact performance. A notable class of bug is memory leak caused by failure to properly deallocate memory.
Freeing memory also invalidates pointers to that memory. Future use of those invalidated pointers is a common source of bugs. These problems are avoided by not using dynamic memory allocation after task initialization.
In flight code, all memory is allocated before the mission begins during initialization. During the mission, the software uses only this pre-allocated memory pool.
cvoid system_init(void) {
    telemetry_buffer = malloc(TELEMETRY_SIZE);
    command_queue = malloc(COMMAND_QUEUE_SIZE);
    sensor_data = malloc(MAX_SENSORS * sizeof(SensorReading));
    
    if (!telemetry_buffer || !command_queue || !sensor_data) {
        abort_mission("Memory allocation failed");
    }
}

RULE 4: NO FUNCTION SHOULD BE LONGER THAN WHAT CAN BE PRINTED ON A SINGLE SHEET OF PAPER
No function should be longer than what can be printed on a single sheet of paper in a standard reference format with one line per statement and one line per declaration. Typically, this means no more than about 60 lines of code per function.
Rationale:
Each function should be a logical unit in the code that is understandable and verifiable as a unit. Excessively long functions are often a sign of poorly structured code. Long functions make code reviews harder and make it harder to verify code correctness by eye or by static analyzer.
The limit of 60 lines is not absolute but serves as a guideline. If a function exceeds this length, it should be reconsidered for refactoring into smaller, more focused functions.
cint process_telemetry_packet(uint8_t* packet, size_t len) {
    assert(packet != NULL);
    assert(len > 0 && len <= MAX_PACKET_SIZE);
    
    if (!validate_checksum(packet, len)) {
        return ERROR_CHECKSUM;
    }
    
    if (!validate_sequence(packet)) {
        return ERROR_SEQUENCE;
    }
    
    return store_telemetry(packet, len);
}

RULE 5: THE ASSERTION DENSITY OF THE CODE SHOULD AVERAGE TO A MINIMUM OF TWO ASSERTIONS PER FUNCTION
The assertion density of the code should average to a minimum of two assertions per function. Assertions are used to check for anomalous conditions that should never happen in real-life executions. Assertions must always be side-effect free and should be defined as Boolean tests.
Rationale:
Statistics for industrial coding efforts indicate that unit tests often find at least one defect per 10 to 100 lines of code written. The odds of intercepting defects increase with assertion density. Use of assertions is often also recommended as part of a strong defensive coding strategy.
Assertions should be used to verify pre-conditions and post-conditions of functions, and can be used to verify intermediate stages of processing. Well-placed assertions help document the code and aid in debugging.
cvoid update_orbit_parameters(orbit_t* orbit, double delta_v) {
    assert(orbit != NULL);
    assert(delta_v >= MIN_DELTA_V && delta_v <= MAX_DELTA_V);
    assert(orbit->eccentricity >= 0.0 && orbit->eccentricity < 1.0);
    
    orbit->velocity += delta_v;
    
    assert(orbit->velocity > 0.0);
    assert(orbit->velocity < ESCAPE_VELOCITY);
}
When assertions are used to check the return values of functions, they should be written to explicitly check for specific error conditions rather than just checking for non-zero or non-null values.

RULE 6: DATA OBJECTS MUST BE DECLARED AT THE SMALLEST POSSIBLE LEVEL OF SCOPE
Data objects must be declared at the smallest possible level of scope.
Rationale:
This rule supports a basic principle of data-hiding. Clearly if an object is not in scope, its value cannot be referenced or corrupted. Similarly, if a bug exists, the fewer the number of statements where the defect can manifest itself, the easier it is to find the defect.
The rule discourages the re-use of variables for multiple, incompatible purposes, which can complicate fault diagnosis.
cvoid process_command_sequence(void) {
    for (int i = 0; i < num_commands; i++) {
        command_t cmd = command_queue[i];
        
        if (validate_command(&cmd)) {
            execute_command(&cmd);
        }
    }
}

RULE 7: THE RETURN VALUE OF NON-VOID FUNCTIONS MUST BE CHECKED BY EACH CALLING FUNCTION
The return value of non-void functions must be checked by each calling function, and the validity of parameters must be checked inside each function.
Rationale:
This is possibly the most frequently violated rule, and therefore somewhat more suspect as a general rule. In its strictest form, this rule means that even the return value of printf statements and file close statements must be checked.
One can make a case, though, for including this rule in the context of mission critical software. In the most critical software, there are no unimportant return values. Even a function that appears simple (like file close) can fail for various reasons that the calling code should be aware of.
cint status = write_telemetry(packet, packet_size);
if (status != SUCCESS) {
    log_error("Telemetry write failed", status);
    increment_error_counter(TELEMETRY_ERROR);
    return status;
}

status = close_telemetry_stream();
if (status != SUCCESS) {
    log_error("Stream close failed", status);
    return status;
}

RULE 8: THE USE OF THE PREPROCESSOR MUST BE LIMITED TO THE INCLUSION OF HEADER FILES AND SIMPLE MACRO DEFINITIONS
The use of the preprocessor must be limited to the inclusion of header files and simple macro definitions. Token pasting, variable argument lists (ellipses), and recursive macro calls are not allowed.
Rationale:
The C preprocessor is a powerful tool, but it can also be a source of problems. Complex macros can hide bugs and make code difficult to understand. They can also interfere with static analysis tools.
All macros must expand into complete syntactic units. Macros should not be used to define data types or to create new control structures.
c#define MAX(a,b) ((a) > (b) ? (a) : (b))
#define ARRAY_SIZE(arr) (sizeof(arr) / sizeof((arr)[0]))

#define BEGIN_CRITICAL_SECTION() disable_interrupts()
#define END_CRITICAL_SECTION() enable_interrupts()

RULE 9: THE USE OF POINTERS SHOULD BE RESTRICTED
The use of pointers should be restricted. Specifically, no more than one level of dereferencing is allowed. Pointer dereference operations may not be hidden in macro definitions or inside typedef declarations. Function pointers are not permitted.
Rationale:
Pointers are easily misused, even by experienced programmers. They can make it hard to follow or analyze the flow of data in a program, especially by tool-based static analyzers. Function pointers, similarly, can seriously restrict the types of checks that can be performed by static analyzers.
By restricting dereferencing to a single level, and by preventing the hiding of dereference operations, the readability of the code is improved and the capability for strong static analysis is enhanced.
cint read_sensor(sensor_t* sensor) {
    assert(sensor != NULL);
    return sensor->value;
}

void update_sensors(sensor_array_t* sensors) {
    assert(sensors != NULL);
    
    for (int i = 0; i < sensors->count; i++) {
        sensors->data[i].value = read_hardware_port(i);
    }
}

RULE 10: ALL CODE MUST BE COMPILED FROM THE FIRST DAY OF DEVELOPMENT WITH ALL COMPILER WARNINGS ENABLED AT THE COMPILER'S MOST PEDANTIC SETTING
All code must be compiled, from the first day of development, with all compiler warnings enabled at the compiler's most pedantic setting. All code must compile with these setting without any warnings. All code must be checked daily with at least one, but preferably more than one, state-of-the-art static source code analyzer and should pass the analyses with zero warnings.
Rationale:
There are several very effective static source code analyzers on the market today, and quite a few freeware tools as well. There simply is no excuse for any software development effort not to make use of this readily available technology. It should be considered routine practice, even for non-critical code development.
The rule of zero warnings applies even in cases where the compiler or the static analyzer gives an erroneous warning: if the compiler or analyzer gets confused, the code causing the confusion should be rewritten so that it becomes more trivially valid.
bashgcc -Wall -Wextra -Werror -Wpedantic -std=c99 -O2 flight_software.c

splint +posixlib -strict flight_software.c

pc-lint flight_software.c

CONCLUSION
These ten rules are designed to be enforceable by strong static analyzers and to support the development of reliable, verifiable code for safety-critical and mission-critical applications.
The rules are minimally intrusive and can be adopted even in existing development efforts. They complement, but do not replace, more comprehensive coding standards such as MISRA-C.
All violations of these rules must be justified in code review and documented. No violation should be accepted without a clear rationale and approval from the software lead.

Reference:
Gerard J. Holzmann, "The Power of 10: Rules for Developing Safety-Critical Code," IEEE Computer, Vol. 39, No. 6, June 2006.