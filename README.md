# SignalSense

Analyze oscilloscope CSV recordings and save plots of calibrated pulses,
stacked signals, and spectra.

## Install Pixi

On Windows, run in PowerShell:

```powershell
Invoke-RestMethod -Uri https://pixi.sh/install.ps1 | Invoke-Expression
```

Restart your terminal after installation.

## Set Up

Open PowerShell in the SignalSense folder and install the dependencies:

```powershell
pixi install
```

If you do not already have a `.env`, create it from the example:

```powershell
Copy-Item .env_example .env
```

Set `DATA_PATH` in `.env` to the folder containing your CSV files or measurement subfolders:

```dotenv
DATA_PATH="C:/Measurements/pulse-data"
```

## Run

From the repository folder:

```powershell
pixi run python -m signalsense
```

By default, subfolders whose names contain `hz` (case-insensitive) are processed.
If no subfolders match, CSV files in `DATA_PATH` itself are processed instead.

Before running, check the calibration and processing settings in `CONFIG` in
[src/signalsense/pulse_analyser.py](src/signalsense/pulse_analyser.py).
Set `subfolder_name_filter` to `None` to process all subfolders.

Plots are saved in the `figures` folder inside `DATA_PATH`.
