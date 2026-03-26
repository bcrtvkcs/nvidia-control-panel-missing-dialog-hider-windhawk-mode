# Hide NVIDIA Control Panel Missing Dialog

<p align="center">
  <img src="https://i.imgur.com/8vaxTpN.png?raw=true" alt="ÆSIR Header Image"/>
</p>

Silences the **"NVIDIA Control Panel not found"** notification that appears in the bottom-right corner every time Windows starts.

## Background

Tools like [NVCleanstall](https://www.techpowerup.com/nvcleanstall/) allow you to strip components from the NVIDIA driver package during installation. Certain options — such as disabling or not installing the NVIDIA Control Panel — break the Control Panel integration intentionally or as a side effect. Once broken, `nvcontainer.exe` detects that the Control Panel is missing or non-functional and displays a dialog on every startup prompting you to reinstall it from the Microsoft Store.

Since the **NVIDIA App** now covers everything the classic Control Panel offered — display settings, GPU overclocking, driver management, and more — there is no practical reason to have the Control Panel installed. The dialog serves no purpose and becomes permanent noise.

## What it does

This mod suppresses the "NVIDIA Control Panel not found" dialog completely. It never appears on screen, neither at startup nor at any other time.

## How it works

The mod hooks into `nvcontainer.exe` and intercepts `ShowWindow` and `SetWindowPos` calls. Any top-level `#32770` dialog whose child windows contain the text "NVIDIA" is immediately blocked from becoming visible. A cache of confirmed dialog handles ensures the detection logic runs only once per window, keeping overhead minimal on subsequent calls.

On mod initialization, any already-visible instance of the dialog is also hidden immediately.

## Installation
1. Download and install [Windhawk](https://windhawk.net/)
2. Open Windhawk
3. Click "Discover"
4. Search for "Hide NVIDIA Control Panel Missing Dialog"
5. Install the mod
6. You're all set!

## Compatibility
- Windows 10 and Windows 11
- Targets `nvcontainer.exe` only
