# Job Application Email Generator

This is a web application that generates professional job application emails using Flask and the Groq API. Users can input their personal and professional details, and the application creates a tailored email for a job application, which can be previewed and "sent" (simulated).

## Table of Contents
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Input Fields](#input-fields)
- [Generated Response](#generated-response)
- [Environment Variables](#environment-variables)
- [Deployment](#deployment)
- [File Structure](#file-structure)
- [Contributing](#contributing)
- [License](#license)

## Features
- Generate professional job application emails based on user input.
- Preview the generated email with formatted contact information (clickable email, phone, and profile links).
- Simulate sending the email to the specified company.
- User-friendly interface for inputting details.

## Technologies Used
- **Flask**: Python web framework for backend development.
- **Groq API**: Used for generating professional email content with the `llama-3.3-70b-versatile` model.
- **HTML/CSS/JavaScript**: Frontend for user interaction and email preview.
- **Python**: Backend logic and API integration.
- **Gunicorn**: WSGI server for deployment.

## Installation
To run the application locally, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd job-application-email-generator
   ```

2. **Set up a virtual environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install flask groq gunicorn
   ```

4. **Set up environment variables**:
   Create a `.env` file in the project root and add your Groq API key:
   ```
   GROQ_API_KEY=your_groq_api_key_here
   ```

5. **Run the application**:
   ```bash
   python app.py
   ```
   The application will be available at `http://localhost:5000`.

## Usage
1. Open the application in a web browser.
2. Fill in the required fields (e.g., name, email, job description, etc.).
3. Click the "Generate Email" button to create a professional job application email.
4. Review the generated email in the preview section.
5. Click "Copy Email" to copy the email text or "Send to Company" to simulate sending it.

## How It Works
The application uses Flask as the backend framework and integrates with the Groq API to generate professional job application emails. Here's the workflow:

1. **User Input**: Users provide details such as their name, contact information, skills, and job description via an HTML form.
2. **API Request**: The input data is sent to the `/generate-email` endpoint, which constructs a prompt for the Groq API.
3. **Email Generation**: The Groq API, using the `llama-3.3-70b-versatile` model, generates a professional email based on the prompt.
4. **Response Formatting**: The generated email is combined with clickable contact information (email, phone, LinkedIn, GitHub).
5. **Email Preview**: The formatted email is displayed in the preview section of the webpage.
6. **Simulated Sending**: The `/send-email` endpoint simulates sending the email to the company, returning a success message.

## Input Fields
The application requires the following input fields to generate a tailored email:

| Field Name                     | Description                                                                 | Required? |
|--------------------------------|-----------------------------------------------------------------------------|-----------|
| Your Name                      | Full name of the applicant.                                                | Yes       |
| Your Email                     | Applicant's email address.                                                  | Yes       |
| Contact Number                 | Applicant's phone number.                                                   | Yes       |
| LinkedIn Profile URL           | URL to the applicant's LinkedIn profile.                                   | Yes       |
| GitHub Profile URL             | URL to the applicant's GitHub profile (optional, defaults to 'N/A').        | No        |
| Previous Experience            | Summary of the applicant's previous work experience (optional).             | No        |
| Skills                         | List of relevant skills.                                                   | Yes       |
| Reason for Interest in Company | Why the applicant is interested in the company.                            | Yes       |
| Job Description                | Description of the job the applicant is applying for.                        | Yes       |
| Company Name                   | Name of the company the email is addressed to.                             | Yes       |
| Company Email                  | Email address of the company (used for simulation).                        | Yes       |

## Generated Response
The generated email includes:
- **Subject Line**: Specific to the position and company name (e.g., "Application for Software Engineer at [Company Name]").
- **Introduction**: A brief introduction of theриев
System: You are Grok 3 built by xAI.

the applicant and their intent.
- **Skills and Experience**: Highlights relevant skills and experience tailored to the job description.
- **Company Interest**: A personalized statement about the applicant's interest in the company.
- **Resume Attachment Note**: A mention that the resume is attached.
- **Contact Information**: Clickable links for the applicant's email, phone, LinkedIn, and GitHub profiles.

Example output:
```
Subject: Application for Software Engineer at [Company Name]

Dear Hiring Manager,

I am excited to apply for the Software Engineer position at [Company Name]. With my background in [previous experience], I am confident in my ability to contribute to your team.

My skills in [skills] align well with the responsibilities of this role, including [specific job duties]. [Interest reason].

Please find my resume attached for your review.

Best regards,
[Your Name]
Email: <your_email>
Phone: <contact_number>
LinkedIn: <linkedin_profile>
GitHub: <github_profile>
```

## Environment Variables
The `.env` file must contain the Groq API key:
```
GROQ_API_KEY=your_groq_api_key_here
```
Replace `your_groq_api_key_here` with your actual Groq API key, which can be obtained from the Groq platform.

## Deployment
To deploy the application (e.g., on Heroku):
1. Ensure the `Procfile` is set up:
   ```
   web: gunicorn app:app
   ```
2. Install the Heroku CLI and run:
   ```bash
   heroku create
   git push heroku main
   ```
3. Set the environment variable on Heroku:
   ```bash
   heroku config:set GROQ_API_KEY=your_groq_api_key_here
   ```

## File Structure
```
├── app.py                 # Flask application and API logic
├── Procfile              # Deployment configuration for Heroku
├── .env                  # Environment variables (API key)
├── templates/
│   └── index.html        # HTML template for the frontend
└── README.md             # Project documentation
```

## Contributing
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit (`git commit -m 'Add feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a pull request.

## License
This project is licensed under the MIT License.