
### Clone 

```
https://github.com/mubashir-cvr/Django-Simple-Blog.git
```


#### Activate Virtual Environment


### Install Requirements

```
pip install -r requirement.txt

```
### Install django-ckeditor

```
pip install django-ckeditor

```


### Settings.py

```
INSTALLED_APPS = [
    ...........
    ...........
    'ckeditor',
    'ckeditor_uploader',
]
```

```
CKEDITOR_UPLOAD_PATH = "uploads/"
```

### Project urls.py

```
urlpatterns = [
    ......
    ......
    path('ckeditor/', include('ckeditor_uploader.urls')),
    ......
    ......
    ]

```

###  model.py

#### Import

```
from ckeditor.fields import RichTextField
from ckeditor_uploader.fields import RichTextUploadingField

```

#### Use

```
class Article(models.Model):
    author = models.ForeignKey("auth.User",on_delete = models.CASCADE,verbose_name = "Article")
    title = models.CharField(max_length = 50,verbose_name = "Title")
    content = RichTextField()
    content_with_uploadImage = RichTextUploadingField()

```

### Customise RichTextField or RichTextUploadingField
#### Settings.py

```
CKEDITOR_CONFIGS = {
    'default': {
        'toolbar': 'Custom',
        'toolbar_Custom': [
            ['Format','Styles'],
            ['Bold', 'Italic', 'Underline','HorizontalRule'],
            ['NumberedList', 'BulletedList', '-', 'Outdent', 'Indent', '-', 'JustifyLeft', 'JustifyCenter', 'JustifyRight', 'JustifyBlock','Youtube','Image'],
            ['Link', 'Unlink'],
            ['RemoveFormat', 'Source'],

        ],
        'extraPlugins':['youtube',],
    }
}

```
#### Model.py 

```
class Content(models.Model):
    article = models.ForeignKey(Article,on_delete = models.CASCADE,verbose_name = "Article")
    title = models.CharField(max_length = 50,verbose_name = "Title")
    content_with_uploadImage = RichTextUploadingField(external_plugin_resources=[('youtube','/static/ckeditor_plugins/youtube/youtube/','plugin.js')])

    def __str__(self):
        return self.title
        
 ```
 
 ##### For Youtube Plugin 
    Download Js Packages from [here](https://ckeditor.com/cke4/addon/youtube)
    And place in static folder and map in model field ****external_plugin_resources=[('youtube','/static/ckeditor_plugins/youtube/youtube/','plugin.js')]****
