
Figure 16.12: Media content development and distribution flow

The following is an example of a prompt to generate a movie script:

```
Action: Write a script for a compelling Law & Order episode in a classic procedural drama style.
Context: This is for Law & Order's flagship show set in New York City following NYPD detectives investigating crimes and the prosecutors who ultimately try the cases. Base the script on fictional characters and events. Focus the plot on an intriguing murder mystery that explores moral dilemmas around crime and justice. Align the tone and dialogue with the show's dramatic yet grounded writing style. Structure the script in a three-act format with an exciting opening scene, plot twists, and a suspenseful climax leading to a just resolution. Describe the settings and character actions vividly. Follow standard screenwriting conventions and formatting.
Script Details:
Approximately 50 scenes
Opening scene introduces the victim and mystery
Detectives pursue leads through witty interrogations
Prosecutors debate legal strategy and ethics
Red herrings before revealing the true perpetrator
Thoughtful closing arguments and courtroom drama
```

If you run the preceding prompt against ChatGPT, you could get something like the following:

```
Title: Law & Order Episode: "Shadows of Deceit"
INT. DARK ALLEY - NIGHT
Rain pours down on a desolate New York City alley. A shadowy figure lurks in the darkness, holding a gleaming knife. JASON HARPER (late 30s, rugged detective) and LUCY MARTIN (early 30s, sharp-witted detective) arrive at the crime scene. Flashing lights and uniformed officers create an eerie atmosphere.
EXT. DARK ALLEY - CONTINUOUS
They discover the lifeless body of SARAH WESTON (early 40s, elegant, with a secret), dressed in a pristine white gown, her face frozen in fear.
JASON
 (whispering) What kind of monster does this?
INT. POLICE STATION - INTERROGATION ROOM - MORNING
Jason and Lucy interrogate EDWARD KINGSLEY (50s, wealthy businessman), the victim's secret lover.
EDWARD
 (sweating) I didn't kill her! I loved her!
….
```

If we want to create visual representations for some of the scenes from the script, we can employ a text-to-image model. For instance, we can provide the following input to a Stable Diffusion model:

```
Rain pours down on a desolate New York City alley. A shadowy figure lurks in the darkness, holding a gleaming knife.
```

The resulting image would resemble the image depicted here:

![](OEBPS/Images/B20836_16_13.png)

Figure 16.13: Storyboarding using text-to-image model

It’s still early days for generative AI-created entertainment, but it is already clear that the tremendous opportunities have attracted many companies to build generative AI tools for media use cases such as storyline generation tools. A generative AI video editing tool from Runway, a company that builds video editing tools, has been used for post-production editing such as in *Everything, Everywhere, All At Once*. However, this type of tool raises questions about intellectual property. If AI creates a new character influenced by a well-known figure, who owns the copywrite? There is also concern about the social impact that this technology will have on creative professionals such as animators, scriptwriters, and visual artists. Some generative AI technologies have taken a more cautious approach to creative content generation. For example, the Claude chatbot tool from Anthropic will block the generation of full-length movie scripts to avoid potential negative consequences.

## Car design workflow

Car design plays an essential role in shaping a high-quality automobile. It encompasses three key domains: exterior design, interior design, and color and trim design. The design team responsible for the exterior of the vehicle develops the proportions, shape, and surface details of the vehicle. The interior designer develops the proportions, shape, placement, and surfaces for the instrument panel, seats, door trim panels, headliner, pillar trims, etc. 

Here, the emphasis is on ergonomics and the comfort of the passengers. Lastly, the trim designer is responsible for the research, design, and development of all interior and exterior colors and materials used on a vehicle.

The design development process for exterior and interior design starts with manual sketches and digital drawings, which form the foundation of concept development. These sketches and drawings undergo rigorous review and approval processes within various layers of management. Subsequently, the concept is rendered into a digital format using a `computer-aided styling` (`CAS`) tool to further refine the style, and the design is transformed into vivid images. After that, industrial plasticine or clay modeling is developed from the images. 

During the design process, it is imperative to maintain alignment with the designer’s stylistic vision while adhering to stringent criteria encompassing performance, manufacturability, and safety regulations. This requires product engineering to work concurrently with the designer to ensure the styling is grounded in various engineering constraints.

One area generative AI can play a role is concept development. Designers can use text-guided prompts, using keywords such as “pronounced spoiler,” “futuristic,” or “aerodynamics,” to swiftly generate car design concepts. General-purpose text-to-image models such as Stable Diffusion, Imagen, Amazon Titan Image Generator and DALLE-2 models have demonstrated immense potential in text-guided concept design. For example, the following prompt example will generate a car exterior concept:

```
Action: Generate a 3D rendering of a futuristic electric sports car exterior concept emphasizing aerodynamics and aggressive styling.
Context: This is an electric sports car aimed at the premium market. Focus on creating an extremely aerodynamic shape with sweeping curves and sharp angles. Make it appear powerful, nimble, and high-tech. Incorporate design elements that maximize battery range by reducing drag and turbulence. The styling should feel bold, exotic, and heavily influenced by fighter jets. Render the concept in a three-quarters front perspective in vibrant red. Add dramatic studio lighting to accentuate the design.
Additional Details:
2-door coupe body style
Emphasize the wide and low visual stance
Large air intakes for brake cooling
Futuristic looking wheels
LED accent lighting
Closed grille since it's an EV
```

The following is one output variation when running the prompt using the Stable Diffusion model from Stability AI:

![](OEBPS/Images/B20836_16_14.png)

Figure 16.14: Sports car concept design using generative AI

It is important to note, however, that these tools can only provide a source of style inspiration and do not address complex engineering and safety considerations integral to actual car design for production. These models need to be enhanced to support image generation while also optimizing specific engineering constraints.

Progress has been made in this area, with examples like drag-guided diffusion models that can render creative car concepts while minimizing drag. Technically, these techniques aim to minimize an auxiliary loss function tied to a particular constraint, such as drag, during the model training and image generation process. As a result, when a car design image is generated, it also aligns with optimized constraints, such as minimizing the drag value.

![](OEBPS/Images/B20836_16_15.png)

Figure 16.15: Generative AI-powered car design flow

Such tools have the potential to greatly enhance the productivity of both car designers and product engineers, enabling them to avoid investing time in impractical car design concepts that cannot be feasibly produced for the market.
