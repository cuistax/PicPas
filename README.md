PicPas 0.6.7
=============
Multi-platform Pascal cross-compiler for Microchip PIC16F microcontrollers.

![Tito's Terminal](http://blog.pucp.edu.pe/blog/tito/wp-content/uploads/sites/610/2017/04/PicPas.png "Título de la imagen")

PicPas is a simple compiler, written in Lazarus, which generates executable code for midrange PIC microcontrollers (the 16F series).

No additional libraries or software required to compile. PicPas generates the *.hex file directly.

PicPas works with a simplified version of the Pascal language, that has been adapted to work with limited resources small devices.

Currently, it only supports basic types. 

It includes a very complete IDE to facilitate the development.

The compiler includes optimization options so the code obtained is fairly compact, as that could generate any commercial compiler.

## Installation

PicPas doesn't need installation, and have not dependencies, except the commons of the operative system, where it's runnig.

To run, it's only needed to download the folder from GitHub. There is a compiled  Windows-32 version (PicPas-win32.exe) and a Ubuntu version (PicPas-linux).

If it's required other platform, it need to be compiled from the source code.

When starting, PicPas could generate warning messsages, if not needed folders exist.

## Hello World

As an example the following code, is to blink a LED on port B:

```
{Sample program to blink a Led on PORTB.7}
{$FREQUENCY 8 MHZ }
{$PROCESSOR PIC16F84A}
program BlinkLed;
var
  PORTB : BYTE absolute $06;
  TRISB : BYTE absolute $86;
  pin: bit absolute PORTB.7;
begin                          
  TRISB := 0;   //all outputs
  while true do 
    delay_ms(1000);
    pin := not pin;
  end;
end.
```

PicPas has not special libraries yet, so the special register names, must be defined in the program, or a unit containing this definitions can be created.

## Language Reference

### Program structure

```
program <Name>;  //optional
uses
  //Units declarations

const
  //Constants declarations

var
  //Variables declarations

//<Procedures declaration>

begin
  //Main program body
end.
```

### Unit structure

```
unit <name>;
interface
uses
  //<units declaration>
const
  //<Constant declaration>
var
  //<Variable declaration>

//<Procedures declaration>

implementation

uses
  //<units declaration>
const
  //<Constant declaration>
var
  //<Variable declaration>

//<Procedures implementation>

end.
```

### Control structures

PicPas doens't follow the common Pascal syntax. Instead, a new Modula-2, style syntax is implemented.

The common control structures have the following forms:

```
IF <condition> THEN 
  <block of code>
END;

IF <condition> THEN 
  <block of code>
ELSE
  <block of code>
END;

IF <condition> THEN 
  <block of code>
ELSIF <condition> THEN 
  <block of code>
ELSE
  <block of code>
END;

WHILE <condition> DO
  <block of code>
END;

REPEAT
  <block of code>
UNTIL <condition>;

FOR  <variable> := <start-value> TO <end-value> DO 
  <block of code>
END;
```

## Limitations

•	Only basic types are implemented: bit, byte, char, boolean and word (limited support).
•	Cannot declare arrays or records.
•	No recursion implemented, Because of the limited hardware resources, available in PIC devices.
•	No float point implemented.
•	No interruption support.

Some of these limitations must be solved in next versions.

## Source Code

The source code is in the folder /Source.

To compile PicPas, it's needed to have the following libraries:

* SynFacilUtils
* MisUtils
* MiConfig
* PicUtils 
* Xpres 

All of them, must be availables on the Web. Check the versions used.

PicPas has been compiled, using the version 1.6.2 of Lazarus. Tested in Windows and Ubuntu.

To have more information about the compiler, check the Technical Documentation (Only in spanish by now).

## Development

PicPas is a free software (GPL license) and it's opened for the collaboration of anyone who is interested. 

There is still, much work for development or documentation, so any help will be ap	preciated.