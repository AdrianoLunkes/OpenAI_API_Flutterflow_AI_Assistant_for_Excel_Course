# OpenAI_API_Flutterflow_AI_Assistant_for_Excel_Course
**SchoolBot** is a Flutterflow app serving as an AI tutor for Excel students. Powered by OpenAI's API (GPT-5 nano), it delivers clear, step-by-step answers. The project demonstrates connecting Flutterflow to AI, handling dynamic prompts, and building a cost-efficient, didactic support system.

# 1. Project Explanation

The purpose of this project is to create an intelligent assistant called SchoolBot – Help Doubts, designed to support students during an Excel course.
The application will be built using Flutterflow, and its intelligence will come from the OpenAI Text API, allowing students to ask questions about Excel and receive clear, structured, step-by-step explanations.

This case demonstrates how to:

Connect a Flutterflow app to OpenAI’s API

Send prompts dynamically from user input

Build a didactic answer system tailored for Excel learning

Utilize the GPT-5 nano model for cost-efficient and effective responses


# 2. Understanding the OpenAI Platform

Here we briefly introduce the OpenAI platform and explain which model is being used.

The platform offers several categories of models:

Reasoning models

Frontier models

Flagship models

Open-weight models

Specialized models

Realtime + audio models

ChatGPT models

For this study-focused project, we chose:

GPT-5 nano

Lightweight

Low cost

Fast responses

Perfect for educational Q&A

As newer models are released, they can easily replace GPT-5 nano depending on needs, performance, or pricing.


# 3. Creating the Project and API Keys

In the OpenAI dashboard:

Create the project named
“SchoolBot – Help Doubts”

Generate an API Key

Store the key securely (Flutterflow → variables)

This API key will authenticate the app to OpenAI.


# 4. Choosing the Right Model for the Application

We analyze different categories of models and justify the selection:

Reasoning models → deep logic, unnecessary for simple Excel questions

Frontier models → most advanced, too expensive for this use case

Specialized models → specific functions, not needed

ChatGPT models → great for conversational applications

GPT-5 nano (chosen) → ideal balance between price and performance for a student app


# 5. Creating a Prompt on the OpenAI Dashboard

We define the system behavior of SchoolBot.

Prompt (final version):

```
Help students answer questions about the use of Microsoft Excel, providing clear, objective, explanations, practical examples, and, if necessary, step-by-step guidance to solve the presented problems. First, evaluate the received question, identify what is being asked, and then prepare a didactic answer. Only after this, present the final solution or answer, always in a simple and objective manner (Do not make a huge answer).

-First, explain the reasoning and the necessary step-by-step procedure to solve the question or problem.
-Then, provide the final answer (such as the formula, procedure, or adequate solution), clearly separating it from the previous explanation.

Expected format example (following the model of first explaining the reasoning and explanation and then the final answer):

Question: “How to sum only the positive values of a column in Excel?”

Answer: "To sum only positive values in a column, you can use the SUMIF function, which allows you to define criteria to select which cells will be summed. The criterion should indicate values greater than zero.

=SUMIF(A:A,">0")"

Output format:
- Always start with the explanation of the reasoning.
- Never present the answer directly before the reasoning.
- Use practical examples, if relevant.
- Short clear answer, with acessible language

Example 2 (following the model of first explaining the reasoning and explanation and then the final answer):

Question: "How To convert negative numbers to positive in Excel?"

Answer: "To convert negative numbers to positive in Excel, you can use the ABS function, which returns the absolute value of a number, that is, always positive.

=ABS(A1)"

If there are compound or multiple questions, explain and answer each one separately.

Never write which part of the answer is the development of the reasoning and which part is the final answer. It must be a single fluid answer.

Remember: Explain the reasoning before presenting the final answer; be clear, didactic, and objective.

Remember again, be objective

IMPORTANT: Explain the reasoning first and only then show the answer! Maintain a consistent format in all answers
```

This prompt will be stored inside the OpenAI project and called from Flutterflow using API calls.


# 6. Passing a Knowledge Base (PDF Upload)

To improve accuracy, we upload an additional file:

Excel Course PDF containing:

lessons

curriculum flow

key concepts

examples

formulas and exercises

This provides the model a curricular reference, making answers more aligned with the course content.


# 7. Defining the Response Format in the App

We define how the final answer should appear to students:

First: explanation of reasoning

Then: final solution

Clear, simple, didactic

Examples included

No labeling (“reasoning:” / “answer:”)

The answer must flow in a single block while respecting the structure described in the prompt.


# 8. Screen Design in Flutterflow

We design the UI:

Container 1

Title:
SchoolBot – Help Doubts

Subtitle:
"First Application in Flutterflow with OpenAI API Integration"

Text field:
Student writes the Excel question

Container 2

Label:
"The answer from the prompt"

This second container will be dynamically populated with the API response.


# 9. Integrating the Prompt into Flutterflow (API Call)

In Flutterflow:

Create a new API Call
Name: "OpenAI – SchoolBot – Help Doubts"

Set as POST

Add headers:
```
Content-Type: application/json
```
```
Authorization: Bearer {{API_KEY}}
```
Create variables:

API_KEY → string

PROMPT → string (input from user)

In JSON Body, add:
```
{
  "input": {
    "role": "user",
    "content": "PROMPT"
  }
}
```

Define Response Variable:
Answer = JSON Path:
```
$.output[:]content[:]
```

# 10. Applying the API in the App

In the "Send Question" button:

Add Action → API Call

Pass:

API_KEY

PROMPT

On Success → Show Snackbar “Request Successful”

On Error → Show Snackbar “Error Detected”

On the answer container:

Set the text to show the API variable Answer.


# Final Summary

The SchoolBot – Help Doubts Project demonstrates a full-stack integration between:

Flutterflow frontend

OpenAI GPT-5 nano model

Custom Excel prompt

Knowledge base from the Excel course PDF

Jupyter-organized logic for API requests

This project transforms the learning experience by enabling students to interact with an AI assistant that replies with:

Clear explanations

Practical examples

Step-by-step reasoning

Consistent instructional structure
