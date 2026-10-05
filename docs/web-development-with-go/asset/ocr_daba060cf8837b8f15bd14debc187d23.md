# 6.3. CREATING A REUSABLE BOOTSTRAP LAYOUT

Listing 6.21: Adding Layout to NewView().
```go
func NewView(layout string, files ...string) +View {
	files = append(files,
	"views/layouts/footer.gohtml",
	"views/layouts/bootstrap.gohtml")
	t, err := template.ParseFiles(files...)
	if err != nil {
		ppanic(err)
	}

	return &View{
	Template: t,
	Layout: layout,
	}
n```

Once again, we have made a change that breaks out code. Drats!

Because we updated the NewView function, we need to update any code that called this function. We were calling NewView from our main function, so so head over to main.go and update the main function using Listing 6.22 as a guide.

We will be using the “bootstrap” layout that we just created for all of our views, which is why it is added in the first argument to both NewView function calls, but due is why by the way we wrote our code we could actually render the home and contact views using different layouts if we wanted to test out the home and website layout.

Listing 6.22: Passing a layout to NewView().
```go
func main() {
homeView = views.NewView("bootstrap",
	"views/home.gohtml",
contactView = views.NewView("bootstrap",
	"views/contact.gohtml")
}
// /...
```

Finally, after making all those incremental changes, our code should