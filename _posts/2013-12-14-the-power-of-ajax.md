---
layout: posts
title: The Power of Ajax
permalink: /posts/the-power-of-ajax
author: vtruong
---

The Power of Ajax
=================

> Let me start off my first post on my thoughts about AJAX.
>
> Since the 1990s, web pages like this current blog were based on HTML pages. What this basically means is for every user action, the user requests for the next page or perhaps even the same page to the server, the server then parses all the assets such as: javascript, css stylesheets and images to build the page and hands off the compiled page to the user. This, of course, was a huge headache for people back in 90s when users were concerned with their bandwidth but that's another story.
>
> Okay. Fast-track to 2013. Everybody is loaded with smartphones. And developers around the world are trying to build their web applications on smartphones. Reloading an entire view to update a live game of the my favourite team, Toronto Maple Leafs is completely unacceptable and will ruin the user experience; since, native applications RARELY have this affect.
>
> AJAX. Asynchronous, Javascript and XML. Solves this problem.
>
>In my fifth internship, I had to use AJAX technology to query different leaderboards from all-time leaders and leaders found in different venues. One of the features that Timeplay provides is to show "more leaders" button. It becomes an issue of user experience when the page must reload to show more leaders if the user clicks on the button. Using AJAX, we are able to keep the "native" feeling of the smartphone within the web application and to show more leaders without reloading the web browser.
>
>AJAX is mainly based on Javascript which communicates different parameters to the server and takes any information from the server in a form of JSON format which then parses it into HTML DOM objects. In Timeplay, I used Javascript and Ruby on Rails to get this baby running! Let's see how we do this..
>
>__jQuery (javascript library - client side (the messenger))__
>
		$.ajax ({
		  type : 'get',
		  url : path_name,
		  data : "data1=" + data1 + "&data2=" + data2,   
		  dataType : 'json',
		  async : false,
		  context : document.body,
		  success : function(response) {
		  // your json array will be found in response
		  // use response to start parsing in this function
		  }
		});
>
>__Ruby on Rails (controller code - server side (the advisor))__
>
		def index
		  @leaders = Leader.all

		  # AJAX calls this and responds back to the javascript's success or failure function handler
		  respond_to do |format|
		    format.html  # index.html.erb
		    format.json  { render :json => @leaders }
		  end
		end
>
>AJAX is beautiful and simple to use. I suggest EVERYONE to use this on their web applications.
>
>Cheers.




