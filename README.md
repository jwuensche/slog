## Slog Logging Library - 1.0.49
Advanced logging library for C/C++ which parses log level from config file and prints log if log level from config is equal or higher than level argument while printing with slog() function.

### Usage
If you want to use slog, you need just two files, slog.c and slog.h
You must include slog.h header file in your code and add slog in Makefile or link it manual.
There is Makefile example in this repository and you can see it and modify.

### Simple API
At first you must initialise slog
```
slog_init("filename", "slog.cfg", 3);
```
First argument "filename" is a filename where logs will be saved.
File name will be generated from argument and also from system date.
Finally file name will be something like that:
```
filename-2015-04-02.log
```
Second argument is config file to be parsed, where is writen slog flags, LOGLEVEL and LOGTOFILE.

Third argument is maximum log level.

### Config file

Slog has its config file 'slog.cfg'

Example:
```
LOGLEVEL 3
LOGTOFILE 1
```
First value is logging level to control which levels of log should print.

Second argument is log to file

Enable   | Disable
---------|---------
1        | 0

If 1 is given, logs will be saved in file, but it wont if argument is 0.


### Print and log something
There is an example how use slog. You can also see, compile and run example.c source file where is full functional examples of slog.
```
slog(0, "[LIVE] Test message with level 0");
```
First argument is log level and second is message to print and/or save. Slog ands strings automatically with \n.

### Version
slog_version() is a function which returns version of slog. If argument is 1, it returns only version and build number. Otherwise it returns full version such as Build number, build name and etc.

Usage:
```
slog(0, "Slog Version: %s", slog_version(0));
```
Output will be something like that:
```
2015.05.01-15:59:58 - Slog Version: 0.2.3 Snapshot Build 16 (May  1 2015)
```

### Output
Here is example output strings of slog
```
2015.05.01-15:59:58 - [LIVE] Test message with level 0
2015.05.01-15:59:58 - [LIVE] Test message with level 1
2015.05.01-15:59:58 - [DEBUG] Test message with level 2
2015.05.01-15:59:58 - [DEBUG] Test message with level 3
2015.05.01-15:59:58 - [LIVE] Test message with char argument: test string
2015.05.01-15:59:58 - [LIVE] Test message with int argument: 69
```
