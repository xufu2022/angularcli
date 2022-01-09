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
