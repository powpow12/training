# Paragraph types

## Hero & Quote

There are many ways to build the Hero and Quote in Drupal. One very common approach is to use a paragraph type. Using a paragraph type will allow us to reuse these components on any page we need to.

Using the instructions below, first create a new paragraph type for the **Hero** and later, another for the **Quote**

{% hint style="info" %}
**TIP:** After the Hero pagraph type has been created, you can reuse its fields in the Quote paragraph type.
{% endhint %}

* From Drupal's Admin Toolbar, click **Structure \| Paragraph Types**
* Click the **Add paragraph type** button

  | Label | Machine name |
  | :--- | :--- |
  | Hero | `hero` |
  | Quote | `quote` |

* Click the **Save and manage fields** button

Add the following fields and settings to the paragraph type:

**NOTE:**: All fields use `1` as the **Allowed Number of values**.

| Field label | Machine name | Field type | Component |
| :--- | :--- | :--- | :--- |
| Title | `field_title` | Text \(Plain\) | hero/quote |
| Eyebrow | `field_eyebrow` | Text \(Plain\) | hero |
| Body | `field_body` | Text \(Plain, long\) | hero/quote |
| Image | `field_image` | Media Reference | hero/quote |
| Call To Action | `field_cta` | Link | hero |
| Name | `field_name` | Text \(Plain\) | quote |
| Job title | `field_job_title` | Text \(Plain\) | quote |
| City | `field_city` | Text \(Plain\) | quote |

For the Image field, set the following configuration:

* **Media type**: `image`

For the CTA field, set the following configuration:

* **Allowed link type**: _Both internal and external links_
* **Allowed link text**: _Required_

## Putting the Hero & Quote paragraphs type to use

Now that the Hero paragraph type is done, it's time to add it to a content type. Paragraphs on their own are useless. They need to be added to other entities such as a content type as an Entity Reference field.

### Adding the Hero & Quote to the Basic Page Content type

Although we can add a paragraph type to any content type, for this exercise we will use the Basic Page content type.

* From Drupal's Admin Toolbar, click **Structure \| Content Types**
* Click the **Manage fields** button next to **Basic Page**
* Click the **Add field** button
* Under the _Add a new field_ dropdown, scroll to the **Reference Revisions** section and choose **Paragraph**

  | Label | Machine name |
  | :--- | :--- |
  | Hero | `field_hero` |
  | Quote | `field_quote` |

* Click the **Save and continue** button
* Change _Allowed number of values\__ to **Limited - 1**
* In the _Reference Type_ section, choose **Hero** or **Quote** under _Paragraph type_
* Click the **Save settings** button

We'll use the Basic Page content type shortly to create a new hero in our site.
