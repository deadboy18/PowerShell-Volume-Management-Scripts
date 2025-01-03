# PowerShell Volume Management Scripts

## Overview
This repository contains two PowerShell scripts to manage audio device volume and mute states on Windows. The scripts use the [`AudioDeviceCmdlets`](https://github.com/frgnca/AudioDeviceCmdlets) PowerShell module to control the default playback audio device.

### Scripts Included
1. **SetVolume70.ps1**:
   - Sets the default playback device volume to 70%.
   - Ensures the device is unmuted.

2. **MuteVolume1.ps1**:
   - Sets the default playback device volume to 1%.
   - Mutes the device.

## Prerequisites
### Install the [`AudioDeviceCmdlets`](https://github.com/frgnca/AudioDeviceCmdlets) Module
1. Open PowerShell with administrative privileges.
2. Install the `AudioDeviceCmdlets` module:
   ```powershell
   Install-Module -Name AudioDeviceCmdlets -Scope CurrentUser
   ```
3. Import the module into your session:
   ```powershell
   Import-Module AudioDeviceCmdlets
   ```
4. Verify installation:
   ```powershell
   Get-Command -Module AudioDeviceCmdlets
   ```
## Usage Instructions
### 1. Set Volume to 70% and Unmute
Run the `SetVolume70.ps1` script:
```powershell
.\SetVolume70.ps1
```

**What it does:**
- Sets the default playback device's volume to 70%.
- Unmutes the playback device.

### 2. Set Volume to 1% and Mute
Run the `MuteVolume1.ps1` script:
```powershell
.\MuteVolume1.ps1
```

**What it does:**
- Sets the default playback device's volume to 1%.
- Mutes the playback device.

## Automating the Scripts
You can use Task Scheduler to automate the scripts:

### Schedule `SetVolume70.ps1` to Run at 7:00 AM
1. Open Task Scheduler (`taskschd.msc`).
2. Create a new task:
   - Set the trigger to run daily at `7:00 AM`.
   - Set the action to run PowerShell:
     ```plaintext
     powershell.exe -ExecutionPolicy Bypass -File "C:\Path\To\SetVolume70.ps1"
     ```

### Schedule `MuteVolume1.ps1` to Run at 10:30 AM
1. Repeat the steps above, but:
   - Set the trigger to run daily at `10:30 AM`.
   - Use the path to `MuteVolume1.ps1` in the action.


## Logs
You can modify the scripts to log their actions by appending output redirection:
```powershell
Set-AudioDevice -PlaybackVolume 70 > "C:\Path\To\Log_SetVolume70.txt" 2>&1
Set-AudioDevice -PlaybackMute $true > "C:\Path\To\Log_MuteVolume1.txt" 2>&1
```

## Troubleshooting
### Common Issues
1. **Module Not Found**:
   - Ensure `AudioDeviceCmdlets` is installed and imported.

2. **Permissions**:
   - Run PowerShell with administrative privileges for best results.

3. **Device Not Detected**:
   - Use the following to check available devices:
     ```powershell
     Get-AudioDevice -List
     ```

## Resources
- [`AudioDeviceCmdlets`](https://github.com/frgnca/AudioDeviceCmdlets): PowerShell module for managing audio devices.


## Contributing
Feel free to fork this repository and submit pull requests for improvements or additional functionality.


## License
This project is licensed under the [MIT License](LICENSE).
```
