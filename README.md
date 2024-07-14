# LLM Zoomcamp
A free online course about building a Q&A system. https://github.com/DataTalksClub/llm-zoomcamp

## Calendar
| Lesson | HW |
|--------|----|
| [Introduction to LLMs and RAG](https://github.com/DataTalksClub/llm-zoomcamp/blob/main/01-intro) | [7/1/2024](https://courses.datatalks.club/llm-zoomcamp-2024/homework/hw1)|
| [OpenSource LLMs](https://github.com/DataTalksClub/llm-zoomcamp/tree/main/02-open-source) | [7/8/2024](https://github.com/DataTalksClub/llm-zoomcamp/blob/main/cohorts/2024/02-open-source/homework.md)
| [Vector Search](https://github.com/DataTalksClub/llm-zoomcamp/tree/main/03-vector-search) | [7/15/2024](https://github.com/DataTalksClub/llm-zoomcamp/blob/main/cohorts/2024/03-vector-search/homework.md)|

## Lesson 1 - Introduction to LLMs and RAG
### Starting env
1. pip install -r requirements.txt
2. export OPENAI_API_KEY="xxxx YOUR KEY FROM OPENAI xxxx"
3. jupyter notebook
4. open browser and load localhost URL
5. docker
docker run -it --rm --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e "xpack.security.enabled=false" docker.elastic.co/elasticsearch/elasticsearch:8.4.3

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

#### Homework and Template RAG
https://github.com/Shiva-Mantri/2024LLMZoomcamp/blob/main/Lesson_1/Homework%201_Introduction.ipynb

## Lesson 2 - OpenSource LLMs

## Lesson 3 - Vector Search
Course: [Vector Search](https://github.com/DataTalksClub/llm-zoomcamp/tree/main/03-vector-search)

### Notes
* Sentence Transformers: https://sbert.net/ (maintained by HuggingFace. also at: https://huggingface.co/models?library=sentence-transformers)
* Evaluation Metrics: https://github.com/DataTalksClub/llm-zoomcamp/blob/main/03-vector-search/eval/evaluation-metrics.md
* 
