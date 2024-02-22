**Task 1:** Please identify the malicious process and confirm process id of malicious process.
6812 [[RogueOne/00-What We Have#^f3d79e|00-What We Have]]

**Task 2:** The SOC team believe the malicious process may spawned another process which enabled threat actor to execute commands. What is the process ID of that child process?
4364 [[RogueOne/00-What We Have#^61c0e4|00-What We Have]]

**Task 3:** The reverse engineering team need the malicious file sample to analyze. Your SOC manager instructed you to find the hash of the file and then forward the sample to reverse engineering team. What's the md5 hash of the malicious file?
5bd547c6f5bfc4858fe62c8867acfbb5 [[RogueOne/00-What We Have#^72b00e|00-What We Have]]

**Task 4:** In order to find the scope of the incident, the SOC manager has deployed a threat hunting team to sweep across the environment for any indicator of compromise. It would be a great help to the team if you are able to confirm the C2 IP address and ports so our team can utilise these in their sweep.
13.127.155.166:8888 [[RogueOne/00-What We Have#^f3d79e|00-What We Have]]

**Task 5:** We need a timeline to help us scope out the incident and help the wider DFIR team to perform root cause analysis. Can you confirm time the process was executed and C2 channel was established?
C2: command and control
10/08/2023 11:30:03 [[RogueOne/00-What We Have#^f3d79e|00-What We Have]]

**Task 6:** What is the memory offset of the malicious process?
0x9e8b87762080 [[RogueOne/00-What We Have#^a6465f|00-What We Have]]

**Task 7:** You successfully analyzed a memory dump and received praise from your manager. The following day, your manager requests an update on the malicious file. You check VirusTotal and find that the file has already been uploaded, likely by the reverse engineering team. Your task is to determine when the sample was first submitted to VirusTotal.
10/08/2023 11:58:10 [[RogueOne/00-What We Have#^0aea0d|00-What We Have]]