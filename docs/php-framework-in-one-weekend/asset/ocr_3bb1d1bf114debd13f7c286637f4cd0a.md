```
class ContactController
{
    protected $theme; 10

    public function __construct(TemplateService $theme) 12 {
        $this->>theme = $theme;
    }

    public function get()
    {
        $content = $this->theme->render('contact.html',[
        'title' => 'Contact'
        ]);
        return new Response($content);
    }

    public function post(Request $request)
    {
    // TODO: validate input and send email
    $content = $this->theme->render('basic.html',[
        'title' => 'Contact',
        'content' => "Thank you for your message.",
        ]);
        return new Response($content);
    }
}
```

# Listing 10.5: src/ContactController.php