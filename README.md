# DriveToMacSync

Automatically synchronize files from Google Drive to your Mac.

DriveToMacSync is a Python-based desktop synchronization project that connects to Google Drive through the Google Drive API and downloads files into a local folder on macOS. The configured workflow checks for changes every 30 seconds.
Project status: This README documents the project configuration discussed so far. Verify the local paths, module names, and command-line options against your current source code before publishing.

Features
- Google Drive API integration
- OAuth 2.0 authentication for a desktop application
- Downloads files from Google Drive to a local Mac folder
- Configurable synchronization interval (30 seconds in the discussed setup)
- Designed for a local folder named PythonAutoSync
- Python implementation
How it works
1. The application starts and authenticates with Google using OAuth.
2. It accesses the Google Drive files allowed by the configured API scopes.
3. It checks Drive for files that need to be synchronized.
4. It downloads eligible files into the configured local destination.
5. It repeats the check at the configured interval.
Google Drive
     |
     | Google Drive API + OAuth 2.0
     v
DriveToMacSync (Python)
     |
     | Download / synchronize
     v
Mac local folder: PythonAutoSync
Project configuration
The previously discussed setup used:
- Project folder: ~/D/DriveToMacSync
- Local destination folder: PythonAutoSync
- Sync interval: 30 seconds
- Google Cloud OAuth application type: Desktop app
These are configuration details, not guaranteed defaults in every version of the code.
Requirements
- macOS
- Python 3
- A Google account with access to the source Drive files
- A Google Cloud project with the Google Drive API enabled
- OAuth 2.0 Desktop app credentials
- The Python dependencies used by this project's source code
Setup
1. Open the project
cd ~/D/DriveToMacSync
2. Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
3. Install dependencies
If the repository contains a requirements.txt file:
pip install -r requirements.txt
If it does not, install the packages imported by your actual source files. Do not guess package versions; record the working environment in requirements.txt.
4. Configure Google Drive API
1. Open the Google Cloud Console: https://console.cloud.google.com/
2. Create or select a Google Cloud project.
3. Enable the Google Drive API.
4. Configure the OAuth consent screen as required for your Google account and testing status.
5. Create an OAuth client ID with application type Desktop app.
6. Download the OAuth client JSON file.
7. Place it where the application expects it. Keep the credentials file private.
The exact credential filename and location depend on the implementation. Never commit OAuth credentials, access tokens, refresh tokens, or private keys to GitHub.
5. Run the application
Use the entry-point file that exists in your repository. For example, if it is named main.py:
python main.py
If your project uses a different entry point, replace main.py with the correct filename.
Configuration
Keep settings such as the local destination, sync interval, and OAuth credential path in a configuration file or environment variables where practical.

Example settings (adapt these names to the implementation):
SYNC_INTERVAL_SECONDS = 30
LOCAL_SYNC_FOLDER = "PythonAutoSync"
Security notes
- Do not upload OAuth client secrets or token files to a public repository.
- Add credential and token files to .gitignore.
- Request only the Google Drive API scopes the application needs.
- Protect the local sync folder with appropriate macOS permissions.
- Review deletion and overwrite behavior before enabling two-way synchronization.
Suggested .gitignore entries:
.venv/
__pycache__/
*.py[cod]
.env
credentials.json
token.json
*.log
.DS_Store
Adjust these entries to match the actual filenames used by your application.
Current scope and limitations
This README describes a Google Drive-to-Mac download/synchronization workflow. It does not assume that the current implementation supports two-way synchronization, conflict resolution, deletion propagation, selective folder rules, or background launch at login. Document those features only after they are implemented and tested.
Troubleshooting
Problem	What to check
OAuth sign-in fails	OAuth client type, consent-screen configuration, API enablement, and credential path
Permission denied	Google account access, API scopes, and macOS folder permissions
Files do not download	Drive API response, selected folder/file IDs, and application logs
Sync does not repeat	Main loop, configured interval, and whether the process is still running
Missing Python package	Activate .venv and install the project's requirements


Roadmap
- [ ] Add robust logging and clear error messages
- [ ] Add configurable source and destination folders
- [ ] Detect changed files efficiently
- [ ] Add duplicate and conflict handling
- [ ] Add optional two-way synchronization
- [ ] Add safe deletion handling and recovery
- [ ] Add macOS launch-at-login support
- [ ] Add automated tests
Contributing
1. Create a feature branch.
2. Make a focused change.
3. Test it on macOS.
4. Update this README when behavior or configuration changes.
5. Open a pull request.
License
No license has been specified yet. Add a LICENSE file before publishing or accepting contributions.
DriveToMacSync — bringing your Google Drive files to your Mac with Python.


















