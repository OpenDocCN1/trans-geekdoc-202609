The most important consideration about the logic layer in PHP is to design it in a modular way. You can design separate classes/functions for the different business rules or functions that the application demands.

In our polls example, we could create a Polls class where we encapsulate all the methods needed for manipulation, such as getting the current poll, adding a poll, voting, getting the options from a poll, and so on. Then, if we decide to add forums to our site or application, we can design and create a new class/module that has absolutely no relationship or dependence on objects before and after it.

# The Presentation Layer

In the presentation layer you add design and layout elements to the content prepared in the logic layer. This is where you generate HTML using CSS, Flash, images, and whatever else design experts want to use to make the application attractive.

Also, client-side code or presentation layer plug-ins give the presentation layer increasing power to share the computing load of the application proper.

# The Explosion of Web Devices

In the beginning, only browsers accessed the web and they were limited in their functionality. Now we have web-enabled devices such as cell phones, pagers, e-mail clients, PDAs, hand helds, POS terminals, data capturing devices, and more. In the near future even small appliances such as microwave ovens and freezers may want to access the web to get data or publish information about their state.

Different devices require different presentation languages. We can have HTML, XHTML, XML vocabularies, WML, and other presentation languages. If there are two devices accepting the same presentation language it is clear that they might require a different kind of content. We cannot compare the screen of a modern PDA with a text display in a fridge. So there will be a requirement for different presentation languages and formats from a dozen different devices accessing a web application.

Don't forget machines, programs accessing the web collecting information. We might have to generate a presentation language for these programs, usually an XML vocabulary or similar. This will enable the creation of web services where organizations provide services and use others to create complex distributed web applications.

While the classic multi-tiered architecture is very useful to separate different layers it is certainly oriented towards HTML-based web applications and sites. We can change the presentation language but this usually implies a lot of effort since we have to recode a lot of functions, some almost impossible in the new presentation language.

Sometimes there will be no mapping between an HTML function and the presentation language we want to use. If this happens then there's something wrong: we are using HTML as our base language. We have built an HTML class and are trying to adapt it to other presentation languages. We tend to force every presentation language to be mapped to HTML and that's impossible. The best solution to the problem of dealing with a lot of different presentation languages seems to be the use of XML.