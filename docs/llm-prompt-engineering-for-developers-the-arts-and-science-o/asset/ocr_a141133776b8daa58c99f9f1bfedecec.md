```
while True: # This will keep the chat session active
print("You: (Type your message. When done, type 'END' on a new \
line)")
lines = []
while True:
line = input()
if line == "END":
break
lines.append(line)
message = '\n'.join(lines)

# Exit the loop (and the program) if the user types 'exit' or '
quit'
if message.lower() in ['exit', 'quit']:
print("Felix: Goodbye!")
break

response = openai.ChatCompletion.create(
model="gpt-3.5-turbo", 
messages=[
{"role": "system", "content": "You are smart and helpful
assistant."},
{"role": "user", "content": "Hi there."},
{"role": "assistant", "content": "Hi there. \n\nI am Felix, the chatbot.\nHow can I help you today?"},
{"role": "user", "content": f"{message}"},
],
temperature=1,
max_tokens=256,
top_p=1,
frequency_penalty=0,
presence_penalty=0
)

try:
print("Felix:", response.choices[0].message.content)
```