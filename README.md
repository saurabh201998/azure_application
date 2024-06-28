# Flask Application Deployment to Azure Web Apps

## Overview

This repository contains a simple Flask application with a single endpoint that returns "Hello, Azure Web Apps!".

## Files

- `app.py`: The Flask application code.
- `requirements.txt`: List of dependencies required for the Flask application.
- `.github/workflows/azure-webapps-python.yml`: GitHub Actions workflow file for CI/CD deployment to Azure Web Apps.

## Deployment Instructions

### Prerequisites

1. **Azure Account**: Ensure you have an Azure account. If not, you can create one [here](https://azure.microsoft.com/en-us/free/).

2. **GitHub Account**: Ensure you have a GitHub account.

### Steps

1. **Clone the Repository**:

    ```sh
    git clone https://github.com/saurabh201998/azure_application.git
    cd azure_application
    ```

2. **Set Up Azure Web App**:

    - Go to the [Azure Portal](https://portal.azure.com/).
    - Click on "Create a resource" and search for "Web App".
    - Click "Create".
    - Fill in the required details:
      - **Subscription**: Select your subscription.
      - **Resource Group**: Create a new resource group or select an existing one.
      - **Name**: Provide a unique name for your web app (e.g., `my-flask-app`).
      - **Publish**: Select "Code".
      - **Runtime stack**: Choose "Python 3.x".
      - **Region**: Select a region close to you.
    - **App Service Plan**:
      - Click on "Create new" under "App Service plan".
      - **Plan name**: Enter a name for the service plan (e.g., `my-flask-plan`).
      - **SKU and size**: Click "Change size" and select the "Dev / Test" tab.
      - Select the "Free F1" tier.
      - Click "Apply".
    - Review your settings and click "Create".

3. **Generate Publish Profile**:

    - In the Azure Portal, navigate to your newly created Web App.
    - Go to "Deployment Center" in the left-hand menu.
    - Under "Settings", select "FTP/Credentials".
    - Click "Get publish profile" to download the publish profile.

4. **Configure GitHub Secrets**:

    - Go to your GitHub repository where your Flask application code is hosted.
    - Click on "Settings".
    - In the left sidebar, click on "Secrets and variables" and then "Actions".
    - Click "New repository secret".
    - Name the secret `AZURE_CREDENTIALS`.
    - Open the downloaded publish profile in a text editor and copy its content.
    - Paste the content into the secret's value field.
    - Click "Add secret".

5. **Push Changes**:

    - Ensure the `main` branch is up to date with all changes.
    - Push any new changes to trigger the GitHub Actions workflow:

    ```sh
    git add .
    git commit -m "Ready for deployment"
    git push origin main
    ```

6. **Verify Deployment**:

    - Go to the "Actions" tab on your GitHub repository.
    - Monitor the workflow execution and check for any errors or issues.
    - Once the workflow completes successfully, navigate to the URL of your Azure Web App to verify that the application is running and returning the expected response.

## Contact

For any issues or questions, please contact Saurabh Ujawane saurabhujawane98@gmail.com.
