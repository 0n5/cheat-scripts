ERB Templating
==============


	<%= %>    # links to a helper
	<%  %>    # control structures

    <%= link_to "[VISIBLE_TEXT]", [FIELD] %>

#### Layout

Main Layout template

	app/views/layouts/application.html.erb

Yield

	<%= yield %>  # renders the target template page


#### Partials

	_form.html.erb

Using partial in another template
	
	<%=  render 'form' %>


#### Views helper functions
	
	$ rake routes   # shows all available routes to use in helper

	link_to                                              # link
	root_path                                            # links to document root /
	edit_[FIELD]_path([FIELD])                           # edit object url path and passes single object in 
	new_[FIELD]											 # new object url path

	stylesheet_link_tag "application", :media => "all"   # links to css stylesheet
	javascript_include_tag "application"				 # links to js files
	csrf_meta_tags                                       # csrf protection

	time_ago_in_words([FIELD].created_at), [FIELD]       # shows in words when the object was created

#### Arguments


Destroy

	method: :delete, data: { confirm: "Are you Sure?" } 


