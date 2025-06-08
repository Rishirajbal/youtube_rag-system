# Windows Setup Guide

This document provides detailed instructions for setting up the YouTube Transcript RAG System on Windows platforms.

## Common Windows Issues and Solutions

### Permission Errors During Installation
```
ERROR: Could not install packages due to an OSError: [WinError 2] The system cannot find the file specified
```

**Recommended Solutions:**
1. Run Command Prompt as Administrator:
   - Right-click Command Prompt
   - Select "Run as administrator"
   - Navigate to project directory
   - Execute installation commands

2. Alternative Installation Methods:
   ```cmd
   pip install --user -r requirements.txt
   ```
   or using virtual environment:
   ```cmd
   python -m venv venv
   venv\Scripts\activate
   pip install -r requirements.txt
   ```

### Module Not Found Errors
```
ModuleNotFoundError: No module named 'youtube_transcript_api'
```

**Troubleshooting Steps:**
1. Verify Python PATH configuration:
   ```cmd
   python -c "import sys; print(sys.path)"
   ```

2. Install package in user directory:
   ```cmd
   pip install --user youtube-transcript-api
   ```

3. Utilize the automated fix script:
   ```cmd
   python fix_windows_install.py
   ```

## Installation Methods

### Recommended: Automated Fix Script
```cmd
python fix_windows_install.py
```

### Alternative: Batch Installation
```cmd
install_windows.bat
```

### Manual Installation Procedure

1. Update pip package manager:
   ```cmd
   python -m pip install --upgrade pip
   ```

2. Install core dependencies:
   ```cmd
   pip install --user flask>=2.3.0
   pip install --user youtube-transcript-api>=0.6.0
   pip install --user pytube>=15.0.0
   pip install --user numpy>=1.24.0
   ```

3. Install PyTorch (CPU version):
   ```cmd
   pip install --user torch>=2.0.0 --index-url https://download.pytorch.org/whl/cpu
   ```

4. Install machine learning packages:
   ```cmd
   pip install --user sentence-transformers>=2.2.0
   pip install --user transformers>=4.30.0
   pip install --user faiss-cpu>=1.7.0
   ```

5. Install remaining requirements:
   ```cmd
   pip install --user langchain>=0.0.300
   pip install --user google-api-python-client>=2.100.0
   ```

### Virtual Environment Method (Most Reliable)
```cmd
python -m venv youtube_rag_env
youtube_rag_env\Scripts\activate
pip install -r requirements.txt
python app.py
```

## Launching the Application

1. Open elevated Command Prompt (Run as Administrator)
2. Navigate to project directory:
   ```cmd
   cd "C:\path\to\youtube_rag-system"
   ```
3. Start the application:
   ```cmd
   python app.py
   ```
4. Access the web interface at:
   ```
   http://localhost:12001
   ```

## Advanced Troubleshooting

### Python Path Recognition Issues
**Resolution:** Add Python to system PATH:
1. Search for "Environment Variables" in Windows
2. Edit System Environment Variables
3. Add Python installation directory to PATH

### SSL Certificate Errors
```cmd
pip install --upgrade certifi
```

### Long Path Limitations
1. Execute `gpedit.msc` as administrator
2. Navigate to: Computer Configuration → Administrative Templates → System → Filesystem
3. Enable "Enable Win32 long paths"

### Antivirus Interference
Temporarily disable security software or add Python to exclusion list

## System Requirements

- Operating System: Windows 10/11
- Python Version: 3.8 or newer
- Memory: 4GB minimum (8GB recommended)
- Storage: 2GB available space
- Internet Connection: Required for initial setup

## Additional Support

1. Verify Python installation:
   ```cmd
   python --version
   ```

2. Check pip version:
   ```cmd
   pip --version
   ```

3. Clear package cache:
   ```cmd
   pip cache purge
   ```

4. Reinstall pip:
   ```cmd
   python -m ensurepip --upgrade
   ```

5. Conda alternative:
   ```cmd
   conda install pytorch torchvision torchaudio cpuonly -c pytorch
   conda install -c conda-forge sentence-transformers
   pip install youtube-transcript-api pytube flask langchain faiss-cpu
   ```

For persistent issues:
1. Consult main README documentation
2. Verify Python version compatibility
3. Attempt fresh virtual environment installation
4. Review Windows Event Viewer logs for detailed errors
