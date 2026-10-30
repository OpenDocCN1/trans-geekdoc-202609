```
# plotly
import plotly.express as px
df = px.data.gapminder().query("year == 2007")
fig = px.sunburst(df, path=['continent', 'country'], values='pop',
color='lifeExp', hover_data=
['iso_alpha'],color_continuous_scale='RdBu',
color_continuous_midpoint=np.average(df['lifeExp'],
weights=df['pop']))
st.plotly_chart(fig, use_container_width=True)
```

Now, open Bash or Terminal, wherever the code is, then run **Streamlit run** Then, open the following link in your browser: **http://Localhost:8051**

![](bbox=[0.12, 0.49, 0.88, 0.91])