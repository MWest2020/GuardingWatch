# GuardingWatch
Check if it can log in, if so, all right. If it can't will mail your support channel. 

## Features

- **Daily Login Checks**: Automates the login process for specified admin sites once a day.
- **Multiple Credential Support**: Allows monitoring of multiple accounts by providing a list of credentials.
- **Secure Credential Storage**: Utilizes GitHub Secrets for secure storage of sensitive information.
- **Email Notifications**: Sends an email to a specified address only if the login check fails, reducing noise and focusing on potential issues.

## Prerequisites

Before setting up GuardianWatch, ensure you have:

- A GitHub account and basic familiarity with GitHub Actions.
- SMTP credentials for an email account that will send notification emails.
- Admin site URLs and credentials you have permission to monitor.

## Setup

### 1. Configure GitHub Secrets

Navigate to your GitHub repository's **Settings** tab, then to **Secrets**. Add the following secrets:

- `CREDENTIALS`: A JSON array containing the usernames and passwords for the login checks. Format: `[{"username": "user1", "password": "pass1"}, ...]`.
- `EMAIL_USERNAME`: The username for the email account to send notifications.
- `EMAIL_PASSWORD`: The password for the email account to send notifications.

### 2. Create the Workflow

In your repository, create a file under `.github/workflows/` named `daily_login_check.yml`. Copy the workflow content provided in the previous instructions into this file.

### 3. Prepare the Python Script

Create a script named `login_check.py` at the root of your repository with the login check logic. Use the provided Python script template and adjust it according to your login mechanism and success criteria.

## Usage

Once set up, GuardianWatch will run automatically based on the schedule defined in the GitHub Actions workflow (default is once a day at 08:00 UTC). You do not need to manually trigger the workflow.

In case of a login failure, the specified email account will receive a notification email detailing the failure, prompting further investigation.

## Customization

- **Changing the Schedule**: Adjust the cron schedule in `daily_login_check.yml` to change the frequency of login checks.
- **Modifying the Login Mechanism**: Update `login_check.py` to accommodate different login processes or success criteria.
- **Alternative Notification Methods**: Modify the workflow to integrate other notification services if email is not preferred.

## Troubleshooting

- Ensure all GitHub Secrets are correctly set with accurate credentials.
- Verify the SMTP settings and credentials if email notifications fail to send.
- Check the Python script for accurate detection of login success or failure based on the admin site's response.

## Contributing

Contributions to GuardianWatch are welcome! Please open an issue or pull request with your suggestions or improvements.

## License

Specify the license under which GuardianWatch is released, ensuring users are aware of their rights to use, modify, and distribute the software.
