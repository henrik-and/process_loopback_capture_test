# Process Loopback Muted Capture Test

This repo use the [Microsoft application loopback sample code](https://github.com/microsoft/windows-classic-samples/tree/main/Samples/ApplicationLoopback) as a starting point. The goal of this project is to validate that, during a process loopback audio capture, muting the captured process will also mute the capture.

Follow the instructions on `//process_loopback_capture/README.md` to build the project. To test it with Chromium, open the Chromium task panel with shift+esc and find the Audio process' id (PID). Start playing audio in Chromium. Now, from the project's root, execute:
```ps
.\process_loopback_capture\cpp\x64\Debug\ApplicationLoopback.exe <PID> includetree Captured.wav
```

The program will capture the process' audio for 10 seconds. Then, it will mute the process audio and keep recording for 10 more seconds. THe captured audio will be saved on `//Captured.wav`. Notice how after the captured process is muted (by the ten-second mark), the recording also gets muted.