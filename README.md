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

### 🛠️ Behind the Scenes: Design & Development Insights

Developing this AI-powered resume reviser involved a thoughtful approach to agent design, navigating specific technical challenges, and ensuring the reliability of AI-generated output.

#### What Approach Did I Take to Design This Agent?

My design philosophy was primarily **output-driven and user-centric**. I began by clearly defining the desired end-user experience: a concise, actionable email providing specific feedback on resume improvement. From this ideal output, we worked backward, identifying the necessary inputs (resume text, job posting) and the intermediate processing steps required. This involved:

1.  **Defining the Core Problem:** Users need tailored resume feedback quickly and efficiently.

2.  **Identifying Key Inputs & Outputs:** Resume text + Job Posting -> Structured Feedback (JSON) -> Formatted Email.

3.  **Leveraging AI for Core Logic:** The AI's role was envisioned as the central "brain" for analysis and recommendation generation.

4.  **Orchestration with n8n:** Using n8n allowed me to visually map the data flow, integrate various services (LLM, email), and handle data transformation between steps.

This iterative approach, focusing on the end-user value, guided the selection of tools and the structuring of the workflow.

#### What Challenges Did I Face in Parsing, Formatting, or Integrating?

Several challenges arose during development:

1.  **Resume Parsing (Initial Input):** Initially, I explored direct PDF resume uploads. However, reliably extracting clean, structured text from diverse PDF formats proved challenging due to varying layouts, fonts, and potential OCR errors. To ensure immediate functionality and a consistent input quality for the LLM, I made the pragmatic decision to **exclude PDF files** from direct upload in this version, relying on users to copy-paste plain text resume content. This allowed me to focus on the core AI analysis and feedback mechanism.

2.  **AI Output Formatting for Email:** While LLMs are excellent at generating text, their raw output (even in Markdown) isn't always perfectly suited for direct insertion into an HTML email. Specifically, converting the AI's array-based feedback (like bullet points) into a properly structured HTML list (`<ul><li>...</li></ul>`) for the email client required careful handling. This necessitated the use of a dedicated **Code node** within n8n. This node acts as a crucial transformation layer, taking the AI's structured data and dynamically generating the necessary HTML markup, ensuring a polished and readable email for the end-user.

3.  **Dynamic Job Posting Extraction:** A significant challenge emerged when attempting to extract job posting content from websites that do not provide dedicated, clean pages for each job (e.g., certain job boards or platforms like LinkedIn, where job details are often embedded within a larger, dynamic page structure). The AI agent sometimes struggled to accurately **discern and isolate the precise job description text** from surrounding navigational elements, advertisements, or unrelated content. This highlights the complexity of web scraping and content extraction when a clear, isolated text block is not consistently available.


#### How Did I Ensure That the AI Returned JSON Reliably?

Ensuring the AI consistently returned data in a structured JSON format was critical for programmatic use in subsequent n8n nodes. I employed a two-pronged strategy:

1.  **Prompt Engineering:** The primary method involved **explicitly specifying the desired JSON schema** within the LLM prompt itself. This included defining the top-level keys (`job-details`, `summary`, `feedback`, etc.). 

2.  **Structured Output Parsing (n8n's AI Agent Node):** I leveraged the capabilities of n8n's AI Agent node. This component allows you to define a **JSON schema** that the AI's output *must* conform to. If the AI deviates from this schema, the parser attempts to correct it or flags an error, acting as a **validation and enforcement layer**. This significantly increased the reliability of receiving parseable JSON, even if the LLM occasionally produced slightly malformed output.

This combination of clear prompting and robust parsing ensures that the AI's valuable insights are delivered in a format that the workflow can consistently process and utilize.

### 💡 Future Enhancements

* **Document Parsing:** Integrate with nodes or custom code to parse resume PDFs/DOCX files directly.

* **Web UI:** Develop a simple frontend web application for a more user-friendly interaction experience.

* **Model Selection:** Allow users to choose different LLM models for analysis.

* **Feedback Tracking:** Implement a system to track the effectiveness of feedback over time.

* **More Output Formats:** Provide feedback in other formats (e.g., downloadable PDF, direct display on a webpage).

Feel free to explore the workflow, fork the repository, and adapt it to your needs! Contributions and suggestions are always welcome.
