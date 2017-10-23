# Complex Number Multi-Tool

The Complex Number Multi-Tool is a program for the HP 35S calculator which combine a few missing functions into one label.

# Features

1. Convert rectangular to polar coordinates.
2. Convert polar to rectangular coordinates.
3. Get the real value.
4. Get the imaginary value.
5. Get the complex conjugate.

# Usage

Run the program with with `XEQ`, `I`, and `ENTER`. The menu will flash three messages with numbers one to five for the five tools. Enter your selection at the prompt.

# Requirements

1. Convert rectangular to polar coordinates:  
   Input: A complex number stored in the `X` register.  
   Output: x theta y, where the x-value is stored in the `X` register, and the y-value is stored in the `Y` register.
2. Convert polar to rectangular coordinates:  
   Input: x theta y, where the x-value is stored in the `X` register, and the y-value is stored in the `Y` register.  
   Output: A complex number stored in the `X` register.
3. Get the real value:  
   Input: A complex number stored in the `X` register.  
   Output: The real value stored in the `X` register.
4. Get the imaginary value:  
   Input: A complex number stored in the `X` register.  
   Output: The imaginary value stored in the `X` register.
5. Get the complex conjugate:  
   Input: A complex number stored in the `X` register.  
   Output: The complex conjugate stored in the `X` register.

# Program Instructions

    I001    LBL I
    I002    SF 10                                   // Set Flag 10 to use EQN as text for menu
    I003    EQN 1=POLAR 2=RECT
    I004    PSE
    I005    EQN 3=REAL  4=IMAG
    I006    PSE
    I007    EQN 5=COMPLEX CONJ
    I008    PSE
    I009    CF 10                                   // Return EQN to normal mode
    I010    INPUT S                                 // Prompt for user selection
    I011    1
    I012    X=Y?                                    // Test if selection is Convert to Polar
    I013    GTO I031
    I014    Roll down                               // Enter the "Roll down" key
    I015    2
    I016    X=Y?                                    // Test if selection is Convert to Rectangular
    I017    GTO I038
    I018    Roll down
    I019    3
    I020    X=Y?                                    // Test if selection is Get Real Value
    I021    GTO I045
    I022    Roll down
    I023    4
    I024    X=Y?                                    // Test if selection is Get Imaginary Value
    I025    GTO I054
    I026    RCL C
    I027    5
    I028    X=Y?                                    // Test if selection is Complex Conjugate
    I029    GTO I063
    I030    RTN                                     // Exit program if no suitable user choice entered
    I031    Roll down                               // Start of Convert to Polar routine
    I032    Roll down
    I033    ENTER
    I034    ARG
    I035    LASTx
    I036    ABS
    I037    RTN                                     // End of Convert to Polar routine
    I038    EQN [REGZ*SIN(REGT),REGZ*COS(REGT)]     // Start of Convert to Rectangular routine
    I039    [1,0]
    I040    x<>y
    I041    *
    I042    EQN LASTx*[0,1]
    I043    EQN REGX+i*REGY                         // Enter "REGX" as four variables, R, E, G, X.
    I044    RTN                                     // End of Convert to Rectangular routine
    I045    Roll down                               // Start of Get Real Value routine
    I046    Roll down
    I047    ENTER
    I048    ARG
    I049    COS
    I050    x<>y
    I051    ABS
    I052    *
    I053    RTN                                     // End of Get Real Value routine
    I054    Roll down                               // Start of Get Imaginary Value routine
    I055    Roll down
    I056    ENTER
    I057    ARG
    I058    SIN
    I059    x<>y
    I060    ABS
    I061    *
    I062    RTN                                     // Start of Get Imaginary Value routine
    I063    Roll down                               // Start of Complex Conjugate routine
    I064    Roll down
    I065    ENTER
    I066    ABS
    I067    x^2                                     // Enter the "X squared" key
    I068    x<>y
    I069    /
    I070    RTN                                     // End of Complex Conjugate routine

# Resources Used

The following programs served as references: 

* Paul Dale's [polar and rectangular conversions](http://www.hpmuseum.org/software/35polrec.htm).
* Antonio Maschio's [complex number decomposition](http://www.hpmuseum.org/cgi-sys/cgiwrap/hpmuseum/archv018.cgi?read=140944).
* Karl Schneider's [complex conjugate conversion](http://www.hpmuseum.org/cgi-sys/cgiwrap/hpmuseum/archv017.cgi?read=121176).
* PickyBart's [single label curve fitting program](https://pickyb.blogspot.co.za/2012/08/curve-fitting-program-for-hp-35s.html) for the menu system.
* Stefan Vorkoetter's [Matrix Multi-Tool](http://www.stefanv.com/calculators/hp35s_matrix_multitool.html) for the name and the idea to consolidate the tools.
