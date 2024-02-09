# issues-with-code-python
why is my command prompt window displaying this? \Desktop\chat_bot3.py", line 59, in &lt;module>     chat_bot_ = Chat_bot()                 ^^^^^^^^ NameError: name 'Chat_bot' is not defined. Did you mean: 'chat_bot'?
import json
from difflib import get_close_matches
from typing import List


def Load_knowledge_base(file_path: str) -> dict:
    with open(file_path, 'r') as file:
        data: dict = json.load(file)
    return data


def save_knowledge_base (file_path: str, data: dict):
    with open(file_path, 'w') as file:
        json.dump(data, file, indent=2)


def find_best_match(user_question: str, questions: list[str]) -> str | None:
    matches: List[str] = get_close_matches(user_question, questions, n=1, cutoff=0.6),
    return matches[0] if matches else None


def get_answer_for_question(question: str, knowledge_base: dict) -> str | None:
    for q in knowledge_base["questions"]:
        if q["question"] == question:
            return q["answer"]


def chat_bot():
    knowledge_base: dict = Load_knowledge_base('knowledge_base.json')

    while True:
       user_input: str = input('You: ')
  
       if user_input.lower() == 'quit':
           break

       best_match: str | None = find_best_match(user_input, [q["question"] for q in knowledge_base["questions"]])

       if best_match:
           answer: str = get_answer_for_question(best_match, knowledge_base)
           print(f'Bot: {answer}')
       else:
           print('Bot: I don\'t know the answer. Can you teach me?')
           new_answer: str = input('Type the answer  or "skip" to skip: ')

           if new_answer.lower() !=  'skip':
               knowledge_base["questions"].append({"question": user_input, "answer": new_answer})
               save_knowledge_base('knowledge_base.json', knowledge_base)
               print('Bot: Thank you! I learned a new response!')

if __name__  ==  '_main_':
 class Chat_bot:
    class Chat_bot:
     def __init__(self):
        # Initialize your chat bot here
        pass

# Instantiate the Chat_bot class
chat_bot_ = Chat_bot()
