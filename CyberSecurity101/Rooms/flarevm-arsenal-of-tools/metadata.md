# Room: FlareVM: Arsenal of Tools

## URL
https://tryhackme.com/room/flarevmarsenaloftools

## Description
FlareVM is a Windows-based virtual machine distribution created by Mandiant (Google Cloud) that transforms a standard Windows installation into a fully equipped malware analysis and reverse engineering workstation. It installs a curated collection of over 200 tools including debuggers, disassemblers, unpackers, memory forensics utilities, network monitors, and file analysis tools — all configured and ready to use. This room takes learners through the entire FlareVM setup process, from creating a fresh Windows virtual machine to running the FlareVM installer and exploring the resulting tool collection. Learners will become familiar with core FlareVM tools such as x64dbg (debugger), IDA Free (disassembler), Process Monitor (procmon), Process Explorer (procexp), HxD (hex editor), Detect It Easy (DIE), PE-bear, RegShot, and many others. The room emphasizes practical workflows: attaching a debugger to a running process, analyzing process behavior with procmon, examining registry changes with RegShot, and unpacking packed binaries. By the end of this room, learners will be comfortable navigating FlareVM's environment and using its toolset for real-world malware analysis tasks.

## Difficulty
Easy

## Time
~1 hour

## Tier
Premium

## Objectives
- Set up a Windows virtual machine suitable for FlareVM installation
- Install FlareVM and verify that all core tools are properly deployed
- Navigate the FlareVM start menu and locate tools by category
- Use x64dbg to step through a simple binary and set breakpoints
- Monitor process activity with Process Monitor and Process Explorer
- Analyze PE file structure with Detect It Easy and PE-bear
- Compare registry snapshots before and after malware execution with RegShot
- Perform basic dynamic analysis of a malware sample in a sandboxed FlareVM environment

## Tools
- FlareVM (Mandiant distribution)
- x64dbg (debugger)
- IDA Free (disassembler)
- Process Monitor (procmon)
- Process Explorer (procexp)
- HxD (hex editor)
- Detect It Easy (DIE)
- PE-bear
- RegShot
- dnSpy (.NET debugger)
- Wireshark

## Concepts
- Windows malware analysis workflow
- Dynamic analysis in a controlled environment
- Process monitoring and introspection
- Registry forensics
- PE file structure analysis
- Debugging concepts (breakpoints, stepping, memory inspection)
- Packer identification and unpacking basics
