# LookUPY
LookUPY is meant to be Chatbot that uses NLP technologies to respond to academics in general at the UPY.
If you are a student who is tired of trying to find an specific teacher in some classroom you don't know
or if you are a teacher that is tired of looking for your student's tutor, then LookUPY should help.
By giving it a prompt using natural language, it should extract the information needed from a database,
and reply to you using natural language as well

# How does it work?
While the chatbot is not deployed yet in a good looking UI, the different notebooks exemplify its entire
intended system, and I recommend using this readme to understand the order in which they should be analyzed.
The pipeline consists of four key sections:
- The multi-label classification model that defines the type of question being asked (BERT)
- The extraction of the required table from a PSQL database
- The extraction of the answer from the table using table question answering (TAPAS)
- The natural language answer generated using text generation (OpenAI)
These sections are in different notebooks, which have comments explaining everything I did. I will guide you
through them.
## Multi-label classification using a trained BERT model
To classify the prompts into their objective, I trained a BERT model using a dataset of multiple prompts
which were already tagged. You can find this in the [mlabel.ipynb](https://github.com/GabrielIslas/lookupy/blob/main/mlabel.ipynb) notebook.
You may also check out my failed first iteration in the [multilabela1](https://github.com/GabrielIslas/lookupy/tree/main/multilabela1) folder.
## Extraction of the required table from a PSQL database
While I am not sure of my database structure yet because it depends on whether the school would lend me their
information on their own format or I have to add it myself into my preferred structure, I went with an example
of my preferred structure, which is a PostgreSQL database. I originally thought I was going to use MySQL until
I realized that structuring schedule information in SQL is convoluted, so I'd rather use the extended types in
PSQL. You can see an example of how I would do it in the [psqlcon.ipynb](https://github.com/GabrielIslas/lookupy/blob/main/psqlcon.ipynb) notebook.
## Table question answering using the TAPAS model
To extract the answer from the PSQL table, I used a table question answering model, in this case, the TAPAS
model by Google. I used an already finetuned version, trained with Wikipedia tables, and it worked surpsingly decent.
I would definitely like to improve here by training it with my own database once I define it.
You can see this in the [tapas.ipynb](https://github.com/GabrielIslas/lookupy/blob/main/tapas.ipynb) notebook.
## Text generation for natural language answer using the OpenAI API
Since the table qa model only extracts the specific answer and I wanted a natural language answer, I used
the OpenAI API to generate it. It is very simple and pretty much just like using ChatGPT. You can see this in
the [anstextgen.ipynb](https://github.com/GabrielIslas/lookupy/blob/main/anstextgen.ipynb) notebook
## Everything together
You can see an example of the process in the background of a UI in the [lookupy.ipynb](https://github.com/GabrielIslas/lookupy/blob/main/lookupy.ipynb)
Ideally, the models would be preloaded and it would be running constantly for its usage, but for now this will do.

# Thank you section
Thanks a lot to the text generation team, Christian and Mauricio, who were together with me doing other projects
with similar technologies. We also had to create a video explaining our process and how we felt throughout it
which you can find [here](https://www.youtube.com/watch?v=NWNq3yg3qls). It was a fun experience and I learned a lot.
Also, two of us were sick and we almost did not send it on time for it to be graded because our lights went out. Great times.

Thanks a lot to teacher Victor Ortiz for providing this project to me; this was very stressful and honestly really annoying at times,
but I would be lying if I didn't this is like the first time in a while where I can say I'm glad I did something due to the amount
of knowledge I got out of it, which is what education is supposed to be worth for. Great!
