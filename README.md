# 🤖 AI-Powered Resume & Job Match Optimizer (n8n Workflow)

<img width="1476" height="550" alt="workflow" src="https://github.com/user-attachments/assets/50348187-1775-417c-b99a-ca3b232b8fae" />

## Get Instant, AI-Driven Feedback to Perfectly Tailor Your Resume for Any Job Posting!

Navigating the modern job market often means meticulously tailoring your resume for each application. This n8n workflow automates that tedious and time-consuming process by leveraging the power of Large Language Models (LLMs) to provide intelligent, actionable feedback.

This AI Agent takes your existing resume content and a target job posting, analyzes them both, and then generates specific suggestions on how to improve your resume's alignment with the job role. The goal is to help you optimize your resume's content, highlight relevant skills, and significantly increase your chances of landing an interview.

### ✨ Key Features

* **Intelligent Analysis:** Deeply analyzes both your resume's content and the requirements outlined in a job description.

* **Personalized Feedback:** Generates specific, actionable recommendations on how to rephrase, emphasize, or add content to your resume.

* **Skill Gap Identification:** Pinpoints skills that might be lacking or need more prominence based on the job role's demands.

* **Automated Delivery:** Delivers comprehensive feedback directly to your inbox as a well-formatted email with bullet points for easy review.

* **Built with n8n:** A flexible and extensible low-code automation platform, making the workflow easy to understand, modify, and extend.

* **OpenAI Integration:** Powered by advanced Large Language Models (LLMs) for nuanced understanding and intelligent feedback generation.

### 🚀 Technologies Used

* **n8n:** Workflow automation platform

* **OpenAI API:** For Large Language Model capabilities 

* **JavaScript:** Used within n8n Code nodes for data manipulation and HTML generation.

* **HTML:** For structuring and formatting the feedback emails.

* **Git/GitHub:** For version control and collaborative development.

### 💡 How to Use / Get Started

This project is an n8n workflow, meaning it runs on an n8n instance.

1.  **Prerequisites:**

    * A running n8n instance (either [n8n Cloud](https://n8n.io/cloud/) or [self-hosted](https://www.google.com/search?q=https://n8n.io/self-hosted/)).

    * An OpenAI API Key (or similar LLM API key).

2.  **Setup Steps:**

    * **Clone this Repository:**

        ```
        git clone [https://github.com/derrickclaye/resume-reviser-ai-agent.git](https://github.com/derrickclaye/resume-reviser-ai-agent.git)
        cd resume-reviser-ai-agent
        
        
        ```

    * **Import Workflow:** Import the `resume-reviser-ai-agent.json` file into your n8n instance.

        * In n8n, go to "Workflows" -> "New" -> "Import from JSON".

    * **Configure Credentials:**

        * **OpenAI API Key:** Create a new "OpenAI API" credential in n8n (under "Credentials" in the left sidebar) and securely add your API key.

        * **Email Service:** Configure your preferred email service (e.g., Gmail, SendGrid) as an n8n credential to enable sending feedback emails.

    * **Activate Workflow:** Ensure the workflow is active in n8n.

3.  **Triggering the Workflow:**

    * The workflow starts with a **Form node**.

    * Provide your **resume text**, **job posting link** and **destination email address** as input to this initial node.

    * The AI agent will process the information and send the detailed feedback to the email address specified in the form node.

    **Note on API Keys (Bring Your Own Key - BYOK):**
    
### 🎯 Why This Project?

This project serves as a practical demonstration of how AI and automation can be combined to solve real-world challenges in career development. It showcases:

* The power of LLMs for structured text analysis and personalized recommendations.

* Effective data manipulation and HTML generation within n8n's Code nodes.

* Building robust and secure automated workflows.

### 💡 Future Enhancements

* **Document Parsing:** Integrate with nodes or custom code to parse resume PDFs/DOCX files directly.

* **Web UI:** Develop a simple frontend web application for a more user-friendly interaction experience.

* **Model Selection:** Allow users to choose different LLM models for analysis.

* **Feedback Tracking:** Implement a system to track the effectiveness of feedback over time.

* **More Output Formats:** Provide feedback in other formats (e.g., downloadable PDF, direct display on a webpage).

Feel free to explore the workflow, fork the repository, and adapt it to your needs! Contributions and suggestions are always welcome.
