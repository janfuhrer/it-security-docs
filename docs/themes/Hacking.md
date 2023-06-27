tags: #symmetric  #social
links:  [[101 AC1 TOC - Intro]] - [[themes/000 Index|Index]]

---
# Hacking

## Technical vulnerabilities

Most important class are software bugs.

* Misconfigured firewalls  
* Hardware bugs  
* Automatically executed software from CD/USB stick on old W32 systems
* etc.

## Typical Bugs

Common bugs include problems in the parsing or rendering logic, or scripting functionality supported by the document format in combination with an interpreter that is insufficiently sandboxed.

## Date and Code

The central goal for an attack is to turn data into code. Memory of a process contains data and code!

* Code may interpret data
* Code may jump to the data
* Pass to other program that parses and runs input (shell)

### SQL Injection

Without prepared statements SQL Injection is possible. If a query uses a variable that can be defined by the user things can go very wrong: 

Example input: `Robert’); DROP TABLE students;--`

## Vulnerability timeline

![[Vulnerability_Timeline.png]]

## Hacking Process (RICE)

1. Reconnaissance
2. Infection
3. Command and Control
4. Exfiltration

---
links:  [[101 AC1 TOC - Intro]] - [[themes/000 Index|Index]]