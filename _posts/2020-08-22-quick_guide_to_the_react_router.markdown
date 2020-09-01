---
layout: post
title:      "Quick Guide to the React Router"
date:       2020-08-22 23:50:38 -0400
permalink:  quick_guide_to_the_react_router
---


*set it up quick and route, route, route!!! Make your SPA contain components which render like separate page depending on which 'route' is in the URL.

![](https://library.kissclipart.com/20181002/prq/kissclipart-dsr-1000n-clipart-d-link-unified-services-router-d-95aeab832e598466.jpg)


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
			
			
		
