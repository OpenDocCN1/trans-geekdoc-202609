# # Checkbox

```
condition = st.checkbox('Do you want?')
if condition:
    st.write('Welcome to my checkbox world!')
```

# # RadioButton

```
sport = st.radio(
"What's your favorite sport?",
('Cricket', 'Football', 'Hockey'))
if sport == 'Cricket':
    st.write('You selected Cricket. 🏏')
elif sport == 'Football':
    st.write('You selected Football. ⚽')
elif sport == 'Hockey':
    st.write('You selected Hockey. 🏑')
else:
    st.write("You didn't select anything.")
```

# # SelectBox

```
option = st.selectbox(
'Which movie type you want to see?',
('Romantic', 'Action', 'Horror'))
st.write('You selected:', option)
```

# # Multiselect

```
options = st.multiselect(
'What are your favorite colors',
['Green', 'Yellow', 'Red', 'Blue'],
['Yellow', 'Red'])
st.write('You selected:', options)
```