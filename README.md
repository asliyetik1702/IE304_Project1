# METU-IE Summer Practice Intelligent Assistant

An interactive, AI-powered virtual consultant developed to help Middle East Technical University (METU) Industrial Engineering students understand the official requirements, deadlines, procedures, and required documents for IE 300 and IE 400 Summer Practices.

This application was developed as a group project for the METU IE 304 course. It uses Streamlit and the OpenAI API with a Retrieval-Augmented Generation approach to provide answers grounded in official departmental documents.

## Project Overview

Students may need to review multiple documents and departmental resources when searching for information about summer practice requirements.

The purpose of this project is to provide a simple conversational interface through which students can ask questions about:

- IE 300 and IE 400 requirements
- Summer practice application procedures
- Required forms and documents
- Company eligibility conditions
- Important deadlines
- Report submission procedures
- Frequently asked questions

The assistant is designed to prioritize official METU Industrial Engineering sources and avoid generating unsupported information.

## Key Features

### Intelligent Document Processing

The application reads and processes official documents stored in the local knowledge base.

Supported document formats include:

- PDF
- DOCX
- PPTX
- TXT

### Retrieval-Augmented Responses

Relevant information is retrieved from the project knowledge base and provided to the language model as context before an answer is generated.

This approach helps ensure that responses remain grounded in official documents.

### Strict Domain Guardrails

The assistant is instructed to answer only questions related to METU Industrial Engineering Summer Practices.

When sufficient information is not available in the knowledge base, the assistant avoids inventing an answer and directs the user to official departmental resources.

### Bilingual Support

The user interface and chatbot responses can be switched between:

- English
- Turkish

### Interactive FAQ Shortcuts

The interface includes one-click questions for frequently requested topics, including:

- Company requirements
- Required documents
- Prerequisites
- Application procedures
- Report submission
- Important deadlines

### Web-Based User Interface

The application is developed with Streamlit and can be accessed through a web browser.

The interface includes:

- A conversational chat area
- Language selection
- Frequently asked question buttons
- Sidebar navigation
- METU-themed visual elements

## System Architecture

The application consists of four main components.

### 1. User Interface

Streamlit manages:

- The web-based chatbot interface
- User input
- Conversation history
- Language selection
- FAQ buttons
- Sidebar components

### 2. Knowledge Base

Official department documents are stored in the `knowledge_base` directory.

The `load_knowledge_base()` function extracts text from supported document formats using:

- `pypdf`
- `python-docx`
- `python-pptx`

### 3. Retrieval and Prompt Construction

The extracted document content is used as the contextual knowledge source for answering student questions.

The user query, retrieved information, and system instructions are combined before being sent to the language model.

### 4. Language Model

The application uses OpenAI's `gpt-4o-mini` model.

A domain-specific system prompt instructs the model to:

- Use only the provided official information
- Avoid unsupported assumptions
- Clearly state when information is unavailable
- Reject unrelated or out-of-scope questions
- Respond in the language selected by the user

## Technology Stack

- Python
- Streamlit
- OpenAI API
- Retrieval-Augmented Generation
- PyPDF
- Python-docx
- Python-pptx
- Git and GitHub

## Project Structure

```text
ie304-chatbot-project/
│
├── app.py
├── requirements.txt
├── metu_logo.png
├── README.md
│
├── knowledge_base/
│   ├── rules.pdf
│   ├── ie400_presentation.pptx
│   └── faq.docx
│
└── .streamlit/
    └── secrets.toml
