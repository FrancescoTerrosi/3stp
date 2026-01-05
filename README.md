# Simple Shell Software Timing Profiler (3STP)

A professional, lightweight, zero-dependency Bash script to profile the execution time of any command or program over a specified number of runs on Linux systems.

## &#128640; Features

* **Statistical Analysis:** Calculates **Average**, **Min**, **Max**, and **Standard Deviation** to give you a complete picture of performance stability.
* **Zero Dependencies:** Uses pure Bash math and `$EPOCHREALTIME`. No other dependencies required.
* **Robust Argument Handling:** Correctly handles commands with flags and quoted arguments (e.g., filenames with spaces).
* **Microsecond Accuracy:** Uses `$EPOCHREALTIME` for high-precision timing.
* **Output Control:** Automatically suppresses `stdout` and `stderr` during profiling, with an optional verbose mode.

## &#128203; Prerequisites

* **Bash 5.0+** (Bourne Again SHell)

## &#128229; Installation

1. Download the script or copy the code into a file named `3stp`.
2. Give the script execution permissions:

```bash
chmod +x 3stp
```

## &#128187; Usage

The basic syntax is:

```bash
./3stp [-v] <n_runs> <command>
```

### Arguments

| Argument | Description |
| :--- | :--- |
| `-v` | **(Optional)** Verbose mode. If included, this **MUST** be the first argument. It prevents the script from silencing the output of the command you are profiling. |
| `n_runs` | The integer number of times to run the command. |
| `command` | The actual command (and its arguments) you wish to profile. |

---

## &#128161; Examples

### 1. Basic Profiling
Run `sleep 0.1` 10 times and get the average execution time. Output is suppressed by default.

```bash
./3stp 10 sleep 0.1
```

### 2. Profiling a Python Script
Run a Python script 50 times to check performance stability.

```bash
./3stp 50 python3 my_script.py
```

### 3. Verbose Mode
If you need to verify that the command is actually working correctly while profiling, use `-v`.

```bash
# -v must be the first argument
./3stp -v 5 ls -la /tmp
```

### 4. Complex Commands
You can pass arguments to the command being profiled just as you normally would.

```bash
./3stp 20 grep -r "TODO" ./src
```

## &#9201; Output Format

The script outputs the **average execution time per run**, formatted in seconds with microsecond precision.

**Example Output:**
```text
------------------------------------------------
Benchmark Results (10 runs)
------------------------------------------------
Cmd:             sleep 0.1
Total Time:      1.040759 s
------------------------------------------------
Avg. Time:       0.104075 s
Avg. Overhead:   0.000006 s (subtracted)
Min:             0.102624 s
Max:             0.104783 s
Std Dev:         0.000565 s
------------------------------------------------
```

## &#129309; Contributing

Feel free to fork this repository and submit pull requests if you want to add features.

## &#128196; License

Open source. Feel free to use and modify.

If you use this tool in your research, articles, or works, **please cite Francesco Terrosi (a.k.a. axer)** as the original author. A link back to this repository is appreciated!
