# django-jstree-widget

    Customizable widget to serve jstree with django.
    Distribute with jstree 3.3.4

## Requirements

- django 1.11 +
- jquery (jsTree requires 1.9.0 or greater in your webpage. You can use a CDN version or include a local copy.)
  
  `<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/1.12.1/jquery.min.js"></script>`

## Usage

- Use widget JsTreeWidget on CharField or derived django form fields.
- Declare your widget with an url to serve ajax 
```python
my_field = forms.CharField(label="My field", widget=JsTreeWidget(url=reverse("api:browse_elements")))
```
- See https://www.jstree.com/docs/json/ "Using AJAX" part to serve ajax response to your widget.
- Ajax request are by nodes, so make sure "children" key in response must be true and not list.


## Configuration

- To use a different theme, include theme folder on accessible django static directory and override widget class Media to serve correct css file.
```python
class BoostrapJsTreeWidget(JsTreeWidget):
    class Media(JsTreeWidget.Media):
        css = {
            'all': (
                'jstree/css/jstree/themes/proton/style.min.css/',
            )
        }

```