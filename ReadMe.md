# DataLog Program

This program is designed to clean DataLog files from an HMI, serve them via `localhost:8000`, and make them accessible for applications like Grafana. Follow the instructions below to install and run the program.

---

## **Installation Guide**

### 1. Extract the ZIP File

After downloading and extracting the ZIP file, you'll find several files and directories. Follow the steps below to set everything up properly.

### 2. Download and Install Python 3.12

1. **Open the "pythonDownload" File**:
   - Locate and open the file named **"pythonDownload"**. This will open your default browser and take you to the Python website to download **Python 3.12**.

2. **Install Python 3.12**:
   - Once the Python installer is downloaded, run the installer.
   - **Important**: During installation, make sure to check the box that says **"Add Python to PATH"**. This ensures Python and `pip` are available from the command line.

3. **Verify Installation**:
   - Open **Command Prompt** (press `Win + R`, type `cmd`, and hit Enter).
   - Type the following commands to ensure Python and `pip` are installed correctly:

     ```bash
     python --version
     pip --version
     ```

   If either command doesn't work, Python may not be correctly added to the PATH. Follow the next step to manually add Python and `pip` to your PATH.

---

### 3. Manually Add Python and pip to PATH (if needed)

1. **Find the Installation Directory**:
   - Navigate to the Python installation folder, typically located at:
     - `C:\Users\<YourUsername>\AppData\Local\Programs\Python\Python312\`

2. **Open Environment Variables**:
   - Right-click on **This PC** (or **Computer**) and select **Properties**.
   - On the left side, click **Advanced system settings**.
   - In the new window, click **Environment Variables**.

3. **Edit the PATH Variable**:
   - In the **System Variables** section, scroll down and find the **Path** variable, then click **Edit**.
   - Click **New** and add the following paths (adjust for your Python version):

     - `C:\Users\<YourUsername>\AppData\Local\Programs\Python\Python312\`
     - `C:\Users\<YourUsername>\AppData\Local\Programs\Python\Python312\Scripts\`

4. **Apply and Test**:
   - Click **OK** to save your changes.
   - Open a new **Command Prompt** and test:

     ```bash
     python --version
     pip --version
     ```

---

### 4. Set Up the Project Environment

1. **Open "Install.bat"**:
   - Locate and run the **"Install.bat"** file in the extracted folder.
   - This script will:
     - **Create a virtual environment** using Python's `venv` tool.
     - **Install all required dependencies** from the `requirements.txt` file.

   You will see `pip` downloading and installing packages. Ensure that the process completes without errors.

---

### 5. Organizing the Log Files

1. **Place Log Files in the Correct Directory**:
   - Place raw log files from the HMI into the `Logs\OriginalLogs` folder.
   - The program will automatically clean these files and output the cleaned logs in the `Logs\CleanedLogs` folder.

---

### 6. Running the Program

1. **Run "Main.py"**:
   - Once everything is set up, run the main program by executing **"Main.py"**.
   - This will start the program and:
     - **Host the current directory** at `http://localhost:8000`.
     - **Automatically clean log files** placed in the `Logs\OriginalLogs` directory.

2. **Access the Hosted Directory**:
   - Open a web browser and go to `http://localhost:8000`.
   - From here, you can access and download files, including cleaned log files, from any machine on your network.

---

### 7. Using Grafana with the Program

1. **Configure Grafana to Access Logs**:
   - In Grafana, set up a **data source** that points to the hosted files at `http://localhost:8000`.
   - Use this URL to access cleaned log files and visualize data directly in Grafana.

---

## **Directory Structure**

```plaintext
DataLogProgram/
├── .venv                  # Virtual environment for Python packages
├── Cleaner.py             # Script for cleaning log files
├── FileHost.py            # Script for hosting files over localhost
├── Main.py                # Main script to start the program
├── Logs/
│   ├── CleanedLogs        # Directory for cleaned log files
│   └── OriginalLogs       # Directory for raw log files
├── requirements.txt       # List of Python dependencies
├── Install.bat            # Script to set up the environment
