# FocusTime 🚀
Landing Page : [Focustime](https://gourabdg47.github.io/assets/code/focustime-landing-page.html#)
FocusTime is a Windows desktop application designed to help you minimize distractions and enhance your productivity by keeping you centered on your chosen tasks. Select the applications you need to work with, set a timer, and FocusTime will help manage other potentially distracting applications based on your preferred blocking mode.

## How FocusTime Helps You 🎯

In a world full of digital distractions, maintaining concentration can be challenging. FocusTime assists you by:

* **Reducing Interruptions:** Actively manages or restricts access to non-essential applications during your work sessions.
* **Promoting Deep Work:** Helps you dedicate uninterrupted blocks of time to your most important tasks.
* **Building Discipline:** Offers different levels of "strictness" to match your focus needs, from gentle reminders to more assertive blocking.
* **Encouraging Healthy Habits:** Includes optional reminders to take breaks, look away from the screen, stand up, and hydrate.
* **Boosting Productivity:** By minimizing task-switching and distractions, you can accomplish more in less time.
* **Providing Motivation:** Displays inspiring quotes to keep you going.

## Features ✨

* **Application Selection:** Lists currently running applications with a visible window, allowing you to choose which ones to focus on.
* **Customizable Focus Duration:** Set your focus session length from 1 minute up to 12 hours.
* **Multiple Focus Modes:**
    * 🔥 **Ember (Beginner – Gentle Heat):** Standard focus session. Allows starting and stopping sessions at will. *Tagline: Start the fire.*
    * ⚒️ **Forge (Intermediate – Structured Pressure):** A more disciplined mode. Once a session starts, it cannot be stopped, and the application cannot be closed until the timer completes. Focus applications are initially minimized to encourage a fresh start. *Tagline: Shape yourself through action.*
    * 🖤 **Obsidian (Advanced – Ruthless Clarity):** The ultimate focus mode. Enforces a 120-minute (2-hour) session. Like Forge, sessions cannot be stopped, and the app cannot be closed prematurely. Focus applications are minimized at the start. *Tagline: No excuses. Just results.*
* **Configurable Blocking Modes:**
    * **Gentle:** Minimizes non-focus and non-whitelisted applications if they come to the foreground. Also gently minimizes other distracting apps in the background.
    * **Moderate:** Minimizes non-focus, non-whitelisted applications and attempts to bring one of your selected focus applications back to the foreground.
    * **Strict:** Attempts to close the main window of non-focus, non-whitelisted applications when they are brought to the foreground, then refocuses on a selected app.
* **Application Whitelisting:** Specify process names (e.g., `explorer`, `code`) that should never be blocked, regardless of the focus session.
* **System Tray Integration:**
    * Option to minimize to the system tray when the main window is closed.
    * Tray icon displays remaining time during a session.
    * Context menu to show the app, stop the session (if allowed by Focus Mode), or exit.
* **Notifications:**
    * Session start and end notifications.
    * Optional health reminders:
        * **Eye Strain (20-20-20 Rule):** Every 20 minutes.
        * **Movement/Posture:** Every 30 minutes.
        * **Hydration:** Every 45 minutes.
* **Performance Customization:** Adjust the interval at which FocusTime checks for distracting applications.
* **Persistent Settings:** Your preferences (block mode, whitelist, etc.) are saved and loaded automatically.
* **Motivational Quotes:** A rotating display of quotes in the footer to keep you inspired.
* **Support Developer Link:** A "Buy Me a Coffee" link in the settings.

## Pre-requisites 🛠️

* **.NET SDK:** Version 6.0 or later (compatible with the `net6.0-windows` target framework used in typical WinForms projects of this nature). You can download it from [dotnet.microsoft.com](https://dotnet.microsoft.com/download).
* **Windows Operating System:** As this is a Windows Forms application utilizing P/Invoke for Windows-specific functions.

## Getting Started 🚀

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd FocusTime # Or your project's directory name
    ```

2.  **Build the project:**
    This command compiles the application.
    ```bash
    dotnet build
    ```

3.  **Run the application (for development/testing):**
    This command will build (if necessary) and run the application directly.
    ```bash
    dotnet run
    ```

4.  **Publish the application (self-contained):**
    This creates a version of the application that includes the .NET runtime, so it can run on machines without the .NET SDK/Runtime installed.
    ```bash
    dotnet publish --configuration Release --runtime win-x64 --self-contained true
    ```
    The output will be in `bin\Release\netX.X-windows\win-x64\publish\`. Look for `FocusTime.exe` (or your project's executable name).

5.  **Create a single, installable .exe (self-contained, single file):**
    This bundles the application and its dependencies (including native libraries if any, and the .NET runtime) into a single executable file.
    ```bash
    dotnet publish -c Release -r win-x64 --self-contained true /p:PublishSingleFile=true /p:IncludeNativeLibrariesForSelfExtract=true
    ```
    The output will be a single `.exe` file in `bin\Release\netX.X-windows\win-x64\publish\`.

## To-Do / Potential Future Features 💡

* [ ] Session statistics and history tracking.
* [ ] Customizable sound notifications for session events and reminders.
* [ ] Advanced blocking:
    * Website blocking (would require more complex integration).
    * Option to kill processes instead of just closing windows in "Strict" mode.
* [ ] Pre-defined focus profiles (e.g., "Work," "Study") with specific apps and settings.
* [ ] Short break timer functionality within focus sessions.
* [ ] Keyboard shortcuts for common actions (start/stop session, open settings).
* [ ] UI Theming and customization options.
* [ ] Detailed logging of blocked application attempts.
* [ ] Ability to schedule focus sessions.
* [ ] Option to automatically start FocusTime on Windows startup.
* [ ] More detailed tooltips and help sections within the app.

## How It Works (Briefly) ⚙️

FocusTime uses the .NET Windows Forms framework. It interacts with the Windows OS to:
* List running processes and their main window titles.
* Monitor the foreground window using `GetForegroundWindow` and `GetWindowThreadProcessId`.
* Manage other applications based on the selected mode:
    * Minimizing windows using `ShowWindow(handle, SW_MINIMIZE)`.
    * Bringing focus applications to the front using `SetForegroundWindow(handle)` and `ShowWindow(handle, SW_RESTORE)`.
    * Attempting to close windows via `process.CloseMainWindow()`.
* Settings are stored locally in an XML file (`%AppData%\FocusTime\settings.xml`).

## Support the Developer 🙏

If you find FocusTime helpful, consider supporting its development:

<p align="center">
  <a href="https://buymeacoffee.com/gourabdg" target="_blank">
    <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" >
  </a>
</p>

The "☕ Buy Me a Coffee" button is also available in the application's settings panel.

---

Happy Focusing!
