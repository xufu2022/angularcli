# tips

rm -rf node_modules

template variable usage

## wrapping 3-rd party services

npm install toastr --save

  need modify angualr.json file in both style and script blocks

     "styles": [
              "node_modules/toastr/build/toastr.min.css",
     "scripts": [
              "node_modules/jquery/dist/jquery.min.js",
              "node_modules/toastr/build/toastr.min.js",

- create toastr services

  to access toastr: (access global object)
 
      import { Injectable } from '@angular/core'

      declare let toastr:any

      @Injectable()
      export class ToastrService {
        success(message: string, title?: string) {
          toastr.success(message, title)
        }
        info(message: string, title?: string) {
          toastr.info(message, title)
        }
        warning(message: string, title?: string) {
          toastr.warning(message, title)
        }
        error(message: string, title?: string) {
          toastr.error(message, title)
        }
      }

ng g c events\event-details -st --inline-style --skip-tests -d
ng g c events\create-event -st --inline-style --skip-tests --flat -d
ng g s events\events-list-resolver --skip-tests --flat -d
ng g s events\events-list-resolver --skip-tests --flat   


resolver : 

    { path: 'events', component: EventsListComponent, resolve: {events:EventListResolver} },

mapping to component data events

       this.events = this.route.snapshot.data['events']

routing active link match **{exact:true}**

    <a [routerLink]="['/events']" routerLinkActive="active" [routerLinkActiveOptions]="{exact:true}">All Events</a>

## Lazy Loading :

Dynamic import

    {
      path: 'user',
      loadChildren: () => import('./user/user.module')
        .then(m => m.UserModule)
    }

Create barrel

  