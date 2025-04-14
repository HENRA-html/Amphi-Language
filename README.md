# Amphi Language Extension

[![Version](https://img.shields.io/badge/version-0.2.0-blue.svg)](https://marketplace.visualstudio.com/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## Overview

The **Amphi Language Extension** brings full language support for **Amphi**—a versatile programming language that seamlessly blends frontend, backend, and system-level operations in one file. With this extension, you get:

- **Custom Syntax Highlighting:** Fully supported keywords, dual-mode blocks, commands, and our new comment style.
- **Dual-Mode Blocks:** Write `{!FRONTEND}` for UI and drawing functions, `{!BACKEND}` for logic and animations, and `{!COMMAND}` for terminal-like file operations.
- **Built-In Functions:** From type inspection (`function: define.dtype(x)` vs. `function: define.dtype(x==)`) to drawing shapes and inserting images (`function: draw: .circle` and `function: draw.img:`).
- **Terminal-Style Commands:** Open, extract, delete, run, move, and edit files or folders with dedicated commands in the `{!COMMAND}` block.
- **Boolean Evaluation:** Use a question mark (`?`) to evaluate expressions as true or false (e.g., `?x=2`).


In Amphi, comments start with `/!` and end with `!/`. Heres a example that covers almost everything:

/! This is a comment in Amphi !/
/! Variable Declaration and Boolean Evaluation !/
x = 2;
?x=2                   /!Evaluates to True because x equals 2!/

/! Math Operations !/
a = 5;
b = 3;
sum = a + b;
function: print.str("Results:" ++ [lbr] ++ "a + b = " ++ sum);

/! Custom Function Definition and Call !/
function: define.str:greet(name),
    function: print.str("Welcome, " ++ name ++ "!");
;
function: greet.str("Developer");

/! Dual-Mode Blocks: Frontend and Backend !/
{!FRONTEND}
    // Draw a circle with specific styling
    function: draw: .circle, id="circle",
    style: color=lightblue, pos=h50%,v50%, size:50px,50px;
    
    /! Insert an image!/
    function: draw.img: src="Circle.png";

{!BACKEND}
    /! Animate the circle with a horizontal slide!/
    function: animate.frontend(id=circle)=hslide,
        hslide.lim=l10%,r10%, hslide.speed=100pxpm;

/! Command Block: Terminal-Style File Operations !/
{!COMMAND}
    command: open: file("untitled.exe") at /Downloads;
    command: extract: file("untitled.zip") at /ExtractedFolder;
    command: delete: file("obsolete.docx") at /Documents;
    command: run: file("installer.sh") at /Scripts;
    command: move: file("data.csv") at /OldFolder to /NewFolder;
    command: edit: file("webpage.amph") at /VSCode;
