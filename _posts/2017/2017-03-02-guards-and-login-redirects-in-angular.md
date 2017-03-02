---
layout:     post
title:      Guards and Login Redirects in Angular
subtitle:   Redirect the user to the page they landed on before being forced to login
date:       2017-03-02
header-img: img/angular-in-action-bg.jpg
---

In your web application, you likely require a user to login to access some functionality. With Angular, we can implement this flow using route guards and the router to help manage redirects.

### Basic Route Guard

Imagine we're building a forum, and we want to ensure that a user is logged in before they can post a new message. You could have the following routes in your application.

```typescript
[
  { path: 'login', component: LoginComponent },
  { path: 'forums', component: ForumsComponent },
  { path: 'forums/:forum_alias', component: ForumComponent },
  { path: 'forums/:forum_alias/post', component: PostComponent }, // Needs to be logged in to access!
  ...
]
```

The route to the post is the one we want to protect, as we want to allow people to read forums without being logged in. To protect it, we'll need to create a route guard, which allows us to run a check (or any number of checks) before a route is activated. 

There are several types of guards, but the one we'll use is the `canActivate` type, which is run before you navigate to a route. These are created like any other service, but they must implement the `canActivate` method. Here is one such example.

```typescript
import { Injectable } from '@angular/core';
import { CanActivate, Router, ActivatedRouteSnapshot, RouterStateSnapshot } from '@angular/router';
import { UserService } from './user.service';

@Injectable()
export class AuthGuardService implements CanActivate {

  constructor(private userService: UserService, private router: Router) {}
  
  canActivate(route: ActivatedRouteSnapshot, state: RouterStateSnapshot) {
    if (this.userService.isValid()) {
      return true;
    } else {
      this.router.navigate(['/login'], {
        queryParams: {
          return: state.url
        }
      });
      return false;
    }
  }
}
```

Once we attach this guard to a route, the `canActivate()` method will fire before the route is activated. The logic will first check if the user is valid (using whatever logic you might need), and if not it will navigate to the login route. Note it also grabs the current URL and sets is as a query parameter, so it would be something like `/login?return=%2Fforums%2F2-introductions` (which the route becomes URL encoded). Now, we can attach this guard to our route.

```typescript
{ path: 'forums/:forum_alias/post', component: PostComponent, canActivate: [AuthGuardService] }, 
```

A route can have multiple guards, so you must assign a new property on the route with an array of guards. Each type of guard has its own property that you'll use.

The last bit is to redirect the user after login, which is handled in the login component. This component has a `login()` method that handles authentication logic, and once authenticated it will redirect you.

```typescript
import { Component } from '@angular/core';
import { UserService } from '../services/user.service';
import { Router, ActivatedRoute } from '@angular/router';

@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css']
})
export class LoginComponent {
  username: string = '';
  password: string = '';
  return: string = '';

  constructor(
    private userService: UserService,
    private router: Router,
    private route: ActivatedRoute) {}

  ngOnInit() {
    // Get the query params
    this.route.queryParams
      .subscribe(params => this.return = params['return'] || '/forums');
  }

  login() {
    if (this.username && this.password) {
      this.userService.login(this.username);
      this.router.navigateByUrl(this.return);
    }
  }
}
```

Here we use `navigateByUrl()` to handle the redirect navigation. This takes a raw URL and routes to it, instead of using the typical `naviate()` method that takes an array of paths. 

There are certainly a number of ways to customize this flow for your own purposes. For example, you could store the return URL in a cookie or localstorage instead. I personally like using the URL because I believe that is where navigation state should be captured.