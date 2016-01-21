---
layout: post
title: "My primer post con jekyll"
date: 2016-01-18
categories: first post
---


#Mi primer post con jekyll
en esta oportunidad, estoy escribiendo en MD para mi primer post con *jekyll*.
luego de mucho tiempo usando como CMS *Wordpress* para mis post personales, he decidido realizar unos cambios

#¿Por que Jekyll?
Varias razones me hacer decdirme por jekyll como herramienta para bloggin.
##

`vamos como sale esta prueba de texto`

<ul>
  {% for post in site.posts %}
      <li>
            <a href="{{ post.url }}">{{ post.title }}</a>
	        </li>
		  {% endfor %}
		  </ul>


