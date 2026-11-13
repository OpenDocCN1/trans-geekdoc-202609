
website layout is the arrangement of all online map elements on a web page. Through the appropriate positioning of online map elements on a web page, we can control the relationship between them to better guide the user experience. Since the user is the only person who clicks the mouse and interacts with the maps, simplicity is the best way to go when considering the user experience and the usability. In other words, the website layout of online maps should be made not only visually appealing but also intuitive, consistent and easy to use.

Layout design depends on the map’s purpose. For map or mapping services or information provision and data query through maps, the map body should occupy a large proportion of a web page, as shown in Figure 4.38. Some online maps cover the entire web page, such as Google Maps and Bing Maps. Navigational and interactive tools are often placed to or on the top left- or right-side of the map body. The placement of all the elements on the page needs to be visually balanced, whether through symmetry or balanced asymmetrical arrangements. Some online mapping websites use toggle-able menus to hide interactive elements and other tools in order to maximise the map display area. In most of these cases, only the map body and menu toggles are visible on the page. A menu toggle displays an option that the user can open (turn on) or close (turn off) a menu. Each time the user clicks the toggle, the status of the option switches. A good example is Earth Weather, which is an animated online map showing real-time global weather conditions, including current wind, weather, ocean and pollution conditions. As shown in Figure 4.39, the online map contains only one visible interactive element – a menu toggle labelled as 'Earth', to show or hide a menu of interactive tools for adding data layers or changing display parameters – placed at the bottom-left corner of the page. Clicking on a location in the map reveals information about the weather conditions at that location from the displayed data layers. The map can be zoomed by turning the mouse wheel and panned by dragging the mouse. The layout is neat and simple but serves the purpose well.

Online maps at a website should have a consistent layout so that they are easy to use and understand for all users. Consistency in layout design is about including common online map elements, keeping these elements in the same position on each map and having them look and behave the same way. A consistent layout should also have a clear, visual hierarchy to the elements on each map so that an online map is not only functional but also attractive from an aesthetic point of view.

In addition, the layout design should be mobile-friendly. More people are using their phones or other devices to access online maps. It is important to consider designing the website with a responsive layout where it can adjust to different screens.

## 4.6.3.2 Design of Interactive Elements

Online maps are generally interactive. Special attention has to be paid to the navigational and interactive elements that conventional static maps do not have. Selection and functional design of these elements depend on the map’s purpose and its specific user group.

The basic navigation tools are zoom controls that change the scale and extent ![](img/8aad3fa01ca9db86bd50bb2edb9a3134_240_0.png)

Figure 4.39 Online map of surface wind from Earth Weather.

Source: https://earth.nullschool.net/.

of the map display. Some of the zoom controls include + and – buttons, zoom level slider (such as the one in Figure 4.38), mouse wheel zoom, ‘Home’ icon to return to initial zoom state, double-click zoom and so on. The common method to navigate around the map is panning by dragging the mouse or by using the arrow keys.

In an online map, moving the mouse over or clicking on a map symbol may lead to further information or data shown in pop-ups. Pop-ups are small windows that appear in the foreground of the online map and display data or information about the features or locations on a layer where a mouseover or clicking event is fired. They are an equally essential and important part of crafting the complete map information experience. A general principle is to keep pop-ups concise and only have one on the screen at a time. They should appear where the user clicks or moves the mouse rather than at the centre of the screen or the centre of the feature.

Usually, complicated online maps have a few filters or search functions. However, the panels should be kept to the absolute minimum size possible. Different panel opacity and colours need to be explored to make the panels to feel integrated with the map.

## 4.6.3.3 Layer Design

Layer design needs to consider the amount of data to be displayed. In order to speed up downloading and draw the data on the screen of a map user in sub-second speeds, the content of an online map should be simple or organised in separate layers, each brought in as one or more separate web services. When an online map involves multiple thematic layers, only one thematic layer should be loaded each time. If all the layers are loaded at the same time, performance may be unacceptably slow. The server requires precious time to iterate through all those layers, retrieve the data, draw it and send the image back to the client. For such an online map, layer toggles are often provided, which allow users to select layers to display.

The content of an online map is also determined by the scale of the map. In principle, online maps have no fixed scale as they can be enlarged or reduced at will through zooming. There are three zooming strategies (Kraak and Brown 2000):

- 1 *Static linear zooming.* Zooming does not change the content of the map. It is mainly used for map images. When enlarged, the map image shows enlarged pixels.
- 2 *Static stepped zooming.* This strategy is primarily used for map tiles. When zooming in or out, the most suitable map tiles for the desired zoom level are retrieved and displayed.
- 3 *Dynamic zooming.* With this strategy, the detail level of the map content changes as the zoom level changes. It requires a direct link between the map and some kind of database.

## 4.6.3.4 Design of Symbology

Maps use symbols to represent spatial information. The effective design of an online map relies on the use of proper symbols and colours in terms of the function of the map and the nature of the data to be visualised, by considering the advantages and limitations of on-screen presentation. In general, the design of symbology for online maps should follow the following principles.

- 1 Map symbols in base layers can be compared with those in conventional base maps so that users can immediately recognise map features without reference to a legend. In other words, the design of base layers should apply established cartographic symbolisation and perception rules. For example, vegetated areas are shaded in green, and roads are represented in single or double lines.

- 2 In thematic layers, the colour, size and shape of symbols are varied so the most important map features are the most obvious, and the quantitative and qualitative relationships between the features are clear. However, the area of on-screen map display is generally smaller than that of a paper map. Therefore, the size of map symbols cannot be too big. Otherwise, they may cover the nearby map features. It cannot be too small to keep the symbols legible either.

- 3 Point symbols and annotations should remain at the same size and at the same location on the map so that they move appropriately when the user zooms, pans or scrolls.

- 4 New visual variables enabled by new technology, such as shadow and transparency, which were not often used in conventional map design, can be applied to enhance map symbol design. For example, shadows can be used to create 3D clickable symbols, enhance the contrast between the thematic and background information or create a raised or depressed effect to a symbol to change its state to let users know that something is happening as a consequence of their actions. Transparency describes the blending of layers with the objects depicted underneath. It can be used to subdue the background in a map in order to enhance the main theme in the foreground.
