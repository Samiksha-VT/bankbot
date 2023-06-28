# bankbot
This bankbot helps the users to check any unknown information regarding bank and the system will works as a bank assistant. The system will get the query from the user and provide the necessary information to the user.

import openai
import gradio

openai.api_key = "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"

messages = [{"role": "system", "content": "You are a financial experts that specializes in banking, finance and investment"}]

def CustomChatGPT(user_input):
    messages.append({"role": "user", "content": user_input})
    response = openai.ChatCompletion.create(
        model = "gpt-3.5-turbo",
        messages = messages
    )
    ChatGPT_reply = response["choices"][0]["message"]["content"]
    messages.append({"role": "assistant", "content": ChatGPT_reply})
    return ChatGPT_reply

demo = gradio.Interface(fn=CustomChatGPT, inputs = "text", outputs = "text", title = "Bank Assistant")

demo.launch(share=True)
