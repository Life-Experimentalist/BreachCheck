# BreachCheck - Sagittarius

> **This project is archived and no longer maintained.** It is kept as a public record of a completed team project; issues and pull requests are not monitored, and the code is not being updated.

<img src="https://socialify.git.ci/Life-Experimentalist/BreachCheck/image?description=1&forks=1&issues=1&language=1&name=1&owner=1&pattern=Circuit%20Board&pulls=1&stargazers=1&theme=Auto" alt="BreachCheck" width="640" height="320" style="align-items: center" />
## Introduction

We strongly advise users to only utilize BreachCheck for their own emails and passwords. Do not misuse this tool or exploit it for malicious purposes. Respect the privacy and security of others by refraining from attempting to check passwords that do not belong to you.

Our aim is to promote responsible and ethical use of BreachCheck to empower individuals in securing their online presence. By adhering to these principles, we can collectively contribute to a safer digital environment for everyone.

You can experience the application [https://breachcheck-sagittarius.streamlit.app/](https://breachcheck-sagittarius.streamlit.app/) which is hosted on Streamlit Sharing Cloud.

## What BreachCheck Sends

BreachCheck queries three public APIs. What leaves your machine differs by check type, so it is stated here explicitly:

| Check | Endpoint | What is transmitted |
| --- | --- | --- |
| Password | `api.pwnedpasswords.com/range/{prefix}` | Only the **first 5 characters** of the password's SHA-1 hash. The remaining suffix is compared locally, so neither the password nor its full hash is sent. |
| Email | `leakcheck.io/api/public?check={email}` | The **full email address**, in the query string. |
| Email | `api.xposedornot.com/v1/check-email/{email}` | The **full email address**, in the URL path. |

The password check uses the Have I Been Pwned k-anonymity range model. The two email checks do not: the address you enter is sent in full to a third-party service.

Note also that on the hosted Streamlit demo, whatever you type reaches the server rendering the app before any hashing happens. For the password check to be k-anonymous end to end, run the tool locally.

## Project Structure

```yaml
BreachCheck/
│
├── Interfaces/
│   └── streamlit_app.py  # Main Streamlit application interface
│
├── api/
│   ├── email_apis.py  # Email lookups (LeakCheck, XposedOrNot)
│   └── password_apis.py  # Password lookups (Have I Been Pwned range API)
│
├── scripts/
│   ├── run_app  # Extensionless script to detect OS and run the appropriate script
│   ├── run_app.sh  # Shell script for Unix-based systems
│   ├── run_app.bat  # Batch script for Windows
│   └── run_app.ps1  # PowerShell script for Windows
│
├── docs/
│   ├── faq_and_contributions.py  # Frequently Asked Questions and Contributions
│   └── terms_and_conditions.py  # Terms and Conditions
│
├── README.md  # Project documentation
├── requirements.txt  # Python dependencies
├── app.py  # Entry point to run the Streamlit application
└── app_complete.py  # Entry point to run the Complete Streamlit application in a single file.
```

Note: This `app_complete.py` file is not used in the project and is a little behind the main `app.py` file. For Contributions, please refer to the `app.py` file.


## Usage

### Prerequisites

Ensure you have Python 3.8 or later installed on your system. (`streamlit==1.40.1` requires Python `>=3.8`, excluding 3.9.7.)

### Installation

1. **Clone the repository:**
    ```bash
    git clone https://github.com/Life-Experimentalist/BreachCheck.git
    cd BreachCheck
    ```

2. **Create a virtual environment (not required):**
    On Linux
    ```bash
    python -m venv venv
    source venv/bin/activate
    ```

    On Windows
    ```ps1
    python -m venv venv
    venv\Scripts\activate
    ```

    On MacOS
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

This will provide clear instructions for setting up and activating a virtual environment on both Windows and macOS.

3. **Install the required packages:**
    ```bash
    pip install -r requirements.txt
    ```

This is for installing the necessary packages to run the Streamlit application and tabulate package required in cli interface.

### Running the Application

To run the Streamlit application there are three ways:
1. You can visit this site [https://breachcheck-sagittarius.streamlit.app/](https://breachcheck-sagittarius.streamlit.app/) to use the Streamlit app which is hosted on Streamlit Sharing Cloud.

2. Using the batch file, use the following command:
    ```bash
    .\scripts\run_app.bat
    ```
3. Using the shortcut file named "Sagittarius" in the root directory of the project. It is the name of the team which made this project.

Note: If you are using the batch file, make sure to run it from the root directory of the project.

3. Don't run the Streamlit app python file manually, it will not work as expected since it is set to open CLI.

4. To modify the user theme of the Streamlit app, you can change the necessary variables [here](.streamlit/config.toml). The theme is set to "dark" by default.

### Running the CLI Interface

To run the CLI interface manually, use the following command:
```bash
python app.py --cli
```

### Complete App in single file

Below is the complete code for the application which is running directly without any support files:

To run this code as a normal Python file to use CLI, use the following command:

```bash
python app_complete.py --cli
```

To run this code as a Streamlit app, use the following command:
```bash
streamlit run app_complete.py
```

## Contributors

### Team Leader
1. [@VKrishna04](https://github.com/VKrishna04)

### Frontend
1. [@harsha4678](https://github.com/harsha4678) <- Figma Landing Page
2. [@longhxirguy](https://github.com/longhxirguy) <- Streamlit Frontend

### APIs Integration
1. [@Karthikkkk123](https://github.com/Karthikkkk123) <- Streamlit Interface
2. [@Saisriram-88](https://github.com/Saisriram-88) <- CLI

### Support / Error Testing
1. [@Jayanth-0703](https://github.com/Jayanth-0703)
