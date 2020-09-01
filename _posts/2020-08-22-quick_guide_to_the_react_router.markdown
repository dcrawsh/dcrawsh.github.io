---
layout: post
title:      "Quick Guide to the React Router"
date:       2020-08-22 23:50:38 -0400
permalink:  quick_guide_to_the_react_router
---


*set it up quick and route, route, route!!! Make your SPA contain components which render like separate page depending on which 'route' is in the URL.

![](data:image/png;base64,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)


---

1. Install that router *boi* npm install react-router-dom and import "the goods"
```import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link
} from "react-router-dom";```

2. Wrap it all up in a <Router> element
```<Router>
        <Nav/>
        <Switch>
          <Route path="/posts/new" exact component={PostInput}/>
          <Route path="/posts/:id" exact component={Post}/>
          <Route path="/" exact component={Root}/>
          <Route path="/about" exact component={About}/>
          <Route path="/posts" exact render={() => <PostsContainer fetchPosts={this.props.fetchPosts} /> } />
        </Switch>
      </Router>```
			-adding the <Switch> element makes sure that only one component is rendered
			-it only renders the first route that matches
			
	3. Add <Route> elements with the path attribute and the component you want to render i.e. ``` <Route path="/posts/new" exact component={PostInput}/>```
	-the exact keyword can be aded to specify that we want an exact match 
	
	4. Create a separate Nav.js with a Nav component
	``` <Link to='/'>
                    <li>Home</li>
                </Link>
                <Link to='/about'>
                    <li>About</li>
                </Link>
                <Link to='/posts'>
                    <li>Posts</li>
                </Link>
                <Link to='/posts/new'>
                    <li>Create New</li>
                </Link>
								```
		-add a to attribute of **to** with the URL.
		
		Following these simple steps should get you going for many basic routes.
			
			
		
