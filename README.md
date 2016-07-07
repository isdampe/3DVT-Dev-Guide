# 3DVT Embedding Guide
This article serves as a technical guide for embedding the [3DVT Viewer](https://v.3dvt.com.au/scottys) in a website.

Looking for a working example? Check out the [3DVT Embed Demo](https://v.3dvt.com.au/embed-demo.html)

## Terms

```
tour_id: Your tour's unique identifier, provided by 3DVT
```

## Embedding your tour into a web page
Tours can be embedded statically by iframe, or dynamically by javascript. Javascript allows you to override default configuration values.

### Embedding with an iframe
In it's simplest form, you can embed your tour by creating an iframe pointing to the correct URL.

For example

```
https://v.3dvt.com.au/{{tour_id}}/
```

If my tour_id was equal to "scottys", we would use the URL

```
https://v.3dvt.com.au/scottys/
```

You can style your iframe using standard CSS where required.

```html
<iframe src="//v.3dvt.com.au/scottys/"></iframe>
```

### Embedding with javascript
If you want more flexibility or power over the tour viewer, you will need to use javascript.

To do this, first you will need to include our javascript embed library, and then create a new tour.

By default, the embed library will search for an element with the ID "tdvt-embed". This is handy if you only use one tour per page.

```html
<div id="tdvt-embed"></div>

<script src="//v.3dvt.com.au/embed.min.js"></script>
<script>
    var tour_id = "scottys";
    var tour = new tdvtEmbed();
    tour.embed({
        tour: tour_id
    });
</script>
```

You can also override these default settings, and inject your tour into an element of your choice.


```html
<div id="scottys-tour"></div>
<div id="sparite-tour"></div>

<script src="//v.3dvt.com.au/embed.min.js"></script>
<script>
    var scottys = new tdvtEmbed();
    scottys.embed({
        tour: "scottys",
        container: "scottys-tour"
    });

    var sparite = new tdvtEmbed();
    sparite.embed({
        tour: "sparite",
        container: "sparite-tour",
        width: "720px",
        height: "480px"
    });
</script>
```

## List of options for tdvtEmbed.embed

```
tour (string)
default: "default"
The tour_id you want to embed, as provided by 3DVT

container (string)
default: "3dvt-embed"
The id of the HTML element where the tour will be injected

width (string)
default: "auto"
The width in CSS format to make the container and iframe

height (string)
default: "auto"
The height in CSS format to make the container and iframe

autorotate (string)
default: "auto"
Set auto rotate to either "on", "off" or "auto" (as set by 3DVT)
```

#### Usage of these options

```javascript
var config = {
    tour: "scottys",
    container: "3dvt-embed",
    width: "720px",
    height: "480px",
    autorotate: "off"
}
```
