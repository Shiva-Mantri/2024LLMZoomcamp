# LLM Zoomcamp
A free online course about building a Q&A system. https://github.com/DataTalksClub/llm-zoomcamp

## Calendar
|Date | Lesson | HW |
|-----|--------|----|
| 6/17/2024 | [Introduction to LLMs and RAG](https://github.com/DataTalksClub/llm-zoomcamp/blob/main/01-intro) | [6/24/2024](https://courses.datatalks.club/llm-zoomcamp-2024/homework/hw1)|

## Lesson 1 - Introduction to LLMs and RAG
### Starting env
1. pip install -r requirements.txt
2. export OPENAI_API_KEY="xxxx YOUR KEY FROM OPENAI xxxx"
3. jupyter notebook
4. open browser and load localhost URL

### Prompting ChatGPT
Build ```prompt``` from ```prompt_template```

#### Prompt & Prompt Template
```
context = ""

for doc in results:
    context = context + f"section: {doc['section']}\nquestion: {doc['question']}, answer:{doc['text']}\n\n"
```
##### Entire Prompt
```
You're a course teaching assistant. Answer the QUESTION based on the CONTEXT from the FAQ database.
Use only the facts from CONTEXT when answering the QUESTION.
If the CONTEXT doesn't contain the answer, output NONE

QUESTION: the course.....ll enroll?

CONTEXT:
section: Gen...ated questions
question: Cours...nute.

section: Gen...estions
question: Cour....pace 
```

#### Prompt Template
```
prompt = prompt_template.format(question=q, context=context).strip()
```

#### Sending Prompt to ChatGPT
```
response =client.chat.completions.create(
    model = 'gpt-4o',
    messages= [{"role":"user", "content": prompt}]
)

response.choices[0].message.content
```