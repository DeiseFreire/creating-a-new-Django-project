# Adding project video

[Please see the project video](https://youtu.be/eXiYM7M3MwU).

# Python on Replit

This is a template to get you started with Python on Replit. It's ready to go so you can just hit run and start coding!

## Running the repl

1. Setup a new secret environment variable (the lock icon) where the key is `SECRET_KEY` and the value is
   a randomly generated token of 32 bits of randomnese. To generate such a token type this into the shell and hit Enter:
```
python
import secrets
secrets.token_urlsafe(32)
```
2. Hit run!

See this 1 minute video for a walkthrough: [https://www.loom.com/share/ecc4e738149f4d1db3bcff01758b3e71](https://www.loom.com/share/341b5574d12040fb9fcbbff150777f1c)

## Installing packages

To add packages to your repl, you can just import directly in the file you want to use the package in, and it will automatically be installed when you press the run button. Like below:
```python
import math
import pandas as pd
```

You could also install packages by using the Replit packager interface in the left sidebar.

## Help

If you need help you might be able to find an answer on our [docs](https://docs.replit.com) page. Feel free to report bugs and give us feedback [here](https://replit.com/support).

## Comandos
Django-admin startproject
python manage.py runserver
django-admin startapp home

## Desenvolvimento

Iniciando o projeto usando um comando Django

Chamar django-admin, e depois um subcomando, startproject.

Nome do projeto: Smartnotes

Criar duas coisas: arquivo manage.py e uma pasta chamada smartnotes 

O arquivo manage.py é o ponto de entrada do projeto. 

Dentro da pasta smartnotes, todos os arquivos são relacionados à configuração do projeto. 

Os três principais arquivos são o arquivo urls.py, para configurar, e as URLs do projeto, e o settings.py. 

O arquivo settings.py. é a base do projeto. 

O arquivo manage.py e o comando runserver para criar um servidor usando as configurações padrão 

INSATALLED_APPS = [
#apps
'home',
]

home > views.py 
from django.shortcuts import render
from django.http import HttpResponse
def home(request):
return HttpResponse('Hello, world!')

smartnotes > urls.py
from django.contrib import admin
from django.urls import path
from home import views
urlpatterns = [
path('admin/', admin.site.urls),
path('home', views.home)
]

Comando django-admin para criar um novo aplicativo chamado home


Abrir o arquivo settings.py. 
Adicionar o nome do aplicativo na variável INSTALLED_APPS. 

home > arquivo views

Importar de django.http import HttpResponse. 
Criar def home que recebe um pedido. 
Retornar um HttpResponse com uma mensagem. 

smartnotes > urls.py 
importar views
dentro dos urlpatterns, adicionar novo caminho views.home. 

A camada de modelo nos permite renderizar as informações provenientes do banco de dados em lindas páginas HTML.

python manage.py runserver
django-admin startapp home
INSATALLED_APPS = [
#aplicativos
'casa',
]

arquivo de views nas notas. 

Adicionar UpdateView. 
Adicionar nova classe, NotesUpdateView que herda de UpdateView. 

/edit 
Alterar a classe de origem e o nome. É isso, é tudo o que precisamos fazer. 

### Botões:
Editar 
Enviar  
Cancelar 
Botão para levar para a página de edição
Deletar

Ciclo completo: listar, detalhar e editar

notes > views.py
from typing import List
from django.shortcuts import render #import da classe render, para renderizar as páginas

from django.http import Http404
from django.views.generic import CreateView, DetailView, ListView, UpdateView
from django.views.generic.edit import DeleteView

from .forms import NotesForm
from .models import Notes

### Método DELETE
class NotesDeleteView(DeleteView):
    model = Notes
    success_url = '/smart/notes'
    template_name = 'notes/notes_delete.html'

### Método PUT
class NotesUpdateView(UpdateView):
    model = Notes
    success_url = '/smart/notes'
    form_class = NotesForm

## Método POST
class NotesCreateView(CreateView):
    model = Notes
    success_url = '/smart/notes'
    form_class = NotesForm

class NotesListView(ListView):
    model = Notes
    context_object_name = "notes"
    template_name = "notes/notes_list.html"

class NotesDetailView(DetailView):
    model = Notes
    context_object_name = "note"
