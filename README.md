
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