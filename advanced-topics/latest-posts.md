# Latest Posts component

We will refer to this as **Latest Posts**, but this could be called many other things \(Card grid, article collection, latest news, etc.\). Whatever the name is, the point is that we have a component repeated multiple times. Some may build this a single component and there is nothing wrong with that approach, however, we could probably get more out of building a single card component first, then repeating it as many times as we want to. By doing this, we have an individual card component we could use not only for this type of content by for various types of content.

![](../.gitbook/assets/latest-posts.png)

### Exercise: Build the Latest Posts component

Once the single Card component has been built, it is time to build the collection of Cards as shown in the image above.

This component will be completely different than the ones we've built thus far. All previous components have been a single item, this one will have an unlimited number of items. Let's start

#### Component's stock content

1. Inside _components_ create a new directory called **latest-posts**
2. Inside the _latest-posts_ directory create a new file called `latest-posts.json`
3. Inside _latest-posts.json_ add the following code:

{% tabs %}
{% tab title="latest-posts.json" %}
```yaml
{
  "heading": {
    "heading_level": "2",
    "modifier": "latest-posts__heading",
    "title": "Latest Posts",
    "url": ""
  },
  "items": [
    {
      "image": "<img src='https://placeimg.com/640/350/places' alt='Card image' />",
      "title": {
        "heading_level": "3",
        "modifier": "card__title",
        "text": "The beauty of nature",
        "url": "#"
      },
      "date": "March 16 2020",
      "body_text": "Curabitur blandit tempus porttitor. Vestibulum id ligula porta felis euismod semper. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Aenean lacinia bibendum nulla sed consectetur.",
      "tags": [
        {
          "text": "Phtography",
          "url": "#"
        },
        {
          "text": "Nature",
          "url": "#"
        },
        {
          "text": "Outdoors",
          "url": "#"
        }
      ],
      "modifier": ""
    },
    {
      "image": "<img src='https://placeimg.com/640/350/places' alt='Card image' />",
      "title": {
        "heading_level": "3",
        "modifier": "card__title",
        "text": "The beauty of nature",
        "url": "#"
      },
      "date": "March 16 2020",
      "body_text": "Curabitur blandit tempus porttitor. Vestibulum id ligula porta felis euismod semper. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Aenean lacinia bibendum nulla sed consectetur.",
      "tags": [
        {
          "text": "Phtography",
          "url": "#"
        },
        {
          "text": "Nature",
          "url": "#"
        },
        {
          "text": "Outdoors",
          "url": "#"
        }
      ],
      "modifier": ""
    },
    {
      "image": "<img src='https://placeimg.com/640/350/places' alt='Card image' />",
      "title": {
        "heading_level": "3",
        "modifier": "card__title",
        "text": "The beauty of nature",
        "url": "#"
      },
      "date": "March 16 2020",
      "body_text": "Curabitur blandit tempus porttitor. Vestibulum id ligula porta felis euismod semper. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Aenean lacinia bibendum nulla sed consectetur.",
      "tags": [
        {
          "text": "Phtography",
          "url": "#"
        },
        {
          "text": "Nature",
          "url": "#"
        },
        {
          "text": "Outdoors",
          "url": "#"
        }
      ],
      "modifier": ""
    }
  ]
}
```
{% endtab %}
{% endtabs %}

There is a lot going on in this file. Let's go over it and you will see that it's actually relatively straight forward.

* First we defined the `heading`  object which will be used as the title for the entire collection.
* At around line 8, we declared an `items` array.  This will help us mimic the array of content to build the collection.
* Each item in the items array represents a card.  Inside each card item we have defined the card's fields \(`image`, `title`, `body_text`, `cta` \).  We have repeated this 3 times to achieve the collection shown in the Latest Posts image above.

#### Component markup

So the data is ready, let's go ahead and add the markup for the component.

1. Inside the _latest-posts_ directory create a new file called `latest-posts.twig`
2. Inside _latest-posts.twig_ add the following code:

{% tabs %}
{% tab title="latest-posts.twig" %}
```php
{{ attach_library('training_theme/latest-posts') }}

<section class="latest-posts{{ modifier ? ' ' ~ modifier }}{{- attributes ? attributes.class -}}"
  {{- attributes ? attributes|without(class) -}}>
  {% if heading %}
    {%
      include '@training_theme/heading/heading.twig' with {
        "heading": heading
      } only
    %}
  {% endif %}

  {% if items %}
    <div class="latest-posts__items">
      {% for item in items %}
          {%
            include '@training_theme/card/card.twig' with {
              "image": item.image,
              "title": item.title,
              "body": item.body,
              "tags": item.tags,
              "modifier": ' latest-posts__item'
            } only
          %}
      {% endfor %}
    </div>
  {% endif %}
</section>

```
{% endtab %}
{% endtabs %}

As I mentioned earlier, this is a unique component and nothing like we've built thus far. Let's review:

* First we attach the component's library.  **Don't forget to create the library.**
* Next we add a `<section>` element to wrap the entire component.  As we've done before, the first and main component wrapper should always use the name of the component as its class \(`latest-posts`\).  In addition we pass the `modifier` and `attributes` placeholders.
* Next we make use of the **heading** component to print the component's main title and we wrap it in an `if` statement to ensure we don't print an empty heading tag.
* Next we check if the `items` array exists, and if so, we create `<div>` to which we pass the class of `latest-posts__items`.  Notice how the classes associated with these elements describe not only what the component they belong to, but also the relationship among the elements.
* **Now, for the first time** we use a `for loop` which is a way for Twig to iterate or loop through an array of content and capture every item in the array.  In this case each item is a card.  For every item we find in the array, we are going to include the Card component and map its fields accordingly.
* Finally, we close the `loop` and we close the `if` statement to complete the logic of the component.

#### Component's styles

We'll skip styles for now, but let's at least create a Sass file for when we need to write styles.

1. Inside the _hero_ directory create a new file called **latest-posts.scss**
2. Inside `latest-posts.scss` add this code:

{% tabs %}
{% tab title="latest-posts.scss" %}
```css
// Import site utilities
@import '../../global/utils/init';
```
{% endtab %}
{% endtabs %}

The code above simply imports global utilities from our theme which will be needed as we start writing styles in Sass. More on this later.

## Compiling the code to generate the Latest Posts

While in your theme's root directory, run the following commands in your command line and press **Return**

`npm run build`

`npm run watch`

{% hint style="info" %}
**TIP:** Since we created a whole new component; if you had the watch task running, it is recommended you stop it by pressing **Ctrl + C** on your keyboard and run the commands above. This will ensure the new component will be generated and all related code will be compiled.
{% endhint %}

In your browser of choice open the following URL: [http://localhost:3000](http://localhost:3000). This will open Pattern Lab where you can find the Hero component under components.

Next, we are going to build the back-end infrastructure in Drupal for this collection. This also will be a unique approach compared to previous components we've built in Drupal.

