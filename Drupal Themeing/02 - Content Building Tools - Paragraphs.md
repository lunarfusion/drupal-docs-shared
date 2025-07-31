
## Paragraphs

**Add the module:**
`composer require 'drupal/paragraphs:^1.19'`

Enable the module in "Extend"

### Create a paragraph type

I am going to create a figure paragraph type using my SDC component. My figure has two fields:

1. image
2. caption

I go to admin > structure > paragraph types > Add paragraph type
I name it "figure"

I create two new fields:
1. a file upload field of type image, which I label "figure image"
2. a plain text field for the caption which I label "figure caption"

In "manage display", I change the labels to "hidden" so they don't show on the page

### Create a new content type
I'm going to create a content type called "Feature Page" and give it permission to use paragraphs.

1. In my site, I go to Structure > Content Types > Add Content Type
2. I created "Feature Page" 
3. I selected "Re-use an existing field" to add a body field (our basic node content)
4. Next, I add another field and I select "Paragraphs" as the field type
5. I named this field "content row"

The paragraph types I've created are listed at the bottom. I select which paragraph types should be available in content row (I selected "figure").

### Build a page with the content type

1. I created a page of content type "Feature Page" and added a content row figure.
2. I inspected the code to get my twig hint for what I should call my paragraph twig template.

### Build the paragraph template

1. In my theme's templates folder, I created a "paragraphs" folder and added a template named paragraph--figure.html.twig
2. I did an *include* to bring in my SDC figure component
3. I specify that the SDC slots of Figure should use content from my figure paragraph type 

#### How to build my include

1. look in admin/structure/paragraphs_type/figure/fields
2. Copy the machine names of each field (field_figure_image, for example)

#### paragraph--figure.html.twig

```
 {{ include ('skeleton:figure', {
  attributes: attributes,
  image: content.field_figure_image,
  caption: content.field_figure_caption,
}) }}
```

Image and caption, which are the slots of our SDC figure component, are listed in the include.
They reference  "content", followed by a ".",  and then the field references (content.field_figure_image, for example).

Now I can add any number of figures to my page of "Feature Page" content type, and they will appear under my body content.

However, they appear vertically one after the other. What if I need a different layout?

### Managing layouts option 1: field template

What if I want to add multiple figures, and I need them to display as flex columns? I can try to do it using the content row field of my feature page content type. 

1. I can inspect my content row, which gives me twig suggestions, and I decide I like "field--field-content-row.html.twig"
2. I can then add a twig template in my theme's "templates" folder with this file name.
3. I copy over the contents of Drupal core's field.html.twig template.
4. I add a wrapping flex row div


#### field--field-content-row.html.twig:

```
{%
  set title_classes = [
    label_display == 'visually_hidden' ? 'visually-hidden',
  ]
%}

{%
  set classes = [
    'row',
  ]
%}

{% if label_hidden %}
  {% if multiple %}
    <div{{ attributes }}>
      {% for item in items %}
        <div{{ item.attributes }}>{{ item.content }}</div>
      {% endfor %}
    </div>
  {% else %}
    {% for item in items %}
      <div{{ attributes }}>{{ item.content }}</div>
    {% endfor %}
  {% endif %}
{% else %}
  <div{{ attributes }}>
    <div{{ title_attributes.addClass(title_classes) }}>{{ label }}</div>
    {% if multiple %}
      <div{{ attributes.addClass(classes)}}>
    {% endif %}
    {% for item in items %}
      <div{{ item.attributes }}>{{ item.content }}</div>
    {% endfor %}
    {% if multiple %}
      </div>
    {% endif %}
  </div>
{% endif %}
```


This causes the figure elements I add to display as flex columns.

### Managing layouts option 2: paragraph within paragraph

Let's try another method.

Let's say that I want content row to be a flexrow, and then I want to be able to put other paragraph types inside of that as the columns, using my SDC components.

#### Create the flex row paragraph type
1. I go to admin/structure/paragraphs_type/add
2. I create a paragraph type called "Flex Row"
3. I add a field to the paragraph type called "Content Column"
4. I select what paragraph types can go in the "Content Column" field (I just selected Figure)

#### Now, I need to edit my Feature Page content type

1. I go to admin/structure/types/manage/feature_page/fields
2. Next to Content Row, I select "edit"
3. Under "paragraph types", I select "Flex Row"

Now, I can create a twig template for my Flex Row field just like I did in the first option. I added a class of "row" to. my wrapping div, and a class of "col" to each item which contains my figure paragraphs.

##### field--paragraph--flex-row.html.twig

```
{%
  set title_classes = [
    label_display == 'visually_hidden' ? 'visually-hidden',
  ]
%}

{%
  set classes = [
    'row'
  ]
%}

{% if label_hidden %}
  {% if multiple %}
    <div{{ attributes }}>
      {% for item in items %}
        <div{{ item.attributes }}>{{ item.content }}</div>
      {% endfor %}
    </div>
  {% else %}
    {% for item in items %}
      <div{{ attributes }}>{{ item.content }}</div>
    {% endfor %}
  {% endif %}
{% else %}
  <div{{ attributes }}>
    <div{{ title_attributes.addClass(title_classes) }}>{{ label }}</div>
    {% if multiple %}
      <div{{ attributes.addClass(classes)}}>
    {% endif %}
    {% for item in items %}
      <div{{ item.attributes }} class="col">{{ item.content }}</div>
    {% endfor %}
    {% if multiple %}
      </div>
    {% endif %}
  </div>
{% endif %}
```


The benefit of the paragraph-within-a-paragraph option is that I can add any number of "flex row" paragraphs, and inside of those, I can add any number of "figures" or whatever my content editors need.