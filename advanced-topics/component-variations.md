# Component Variations

Component variations are instances of a component with minor or big changes in look and/or behavior. Component variations are a great way to build new components using existing components to avoid code repetition.

Let's take a look at the Card component for example. Here are two different ways in which this component will be displayed:

![Default Card component](../.gitbook/assets/card.png)

![Example of Card variation](../.gitbook/assets/card-wide.png)

## Planning for component variations

Looking at the two cards above, we see that they are practically the same card component but with changes for each variation. There are many factors that determine if a component could be used as the base for variations.

* Does the proposed variation have the overall look and feel of the original component?
* Are there common patterns \(fields, markup, layout, etc.\) that can facilitate a variation vs. a whole new component?
* Does the component behavior and layout lend themselves to new variations without altering markup or sacrificing accessibility or user experience?
* Can I achieve the variations with a CSS Modifier class or Twig blocks?

These are questions you should ask yourself before deciding to create component variations. Although technically there are ways a component variation can be created, this does not mean you should. If not properly planned, you could paint yourself in a corner when your components have been over engineered in an effort to accommodate for variations. I would much rather build separate components and make the integration easy, than trying to build over complicated variations that will present issues in the long run with integration or implementation.

In the next page we will dive deeper into effectively creating the Card variations we see above.

