# Ng2-State
### Angular 2 state management service module

## Install

```
npm install --save ng2-state
```

## Use

```app.module.ts```

```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { Ng2StateModule } from 'ng2-state';

import { AppComponent } from './app.component'

@NgModule({
  imports: [
    BrowserModule,
    Ng2StateModule
  ],
  declarations: [
    AppComponent
  ],
  bootstrap: [ AppComponent ]
})
export class AppModule { }

```

```app.component.ts```

```
import { Component } from '@angular/core';
import { Ng2StateService } from 'ng2-state';

@Component({
  selector: 'app',
  templateUrl: './app.component.html'
})

export class AppComponent {

  constructor(
    private state: Ng2StateService
  ) {
    this.state.subscribe('HELLO_WORLD', payload => {
      console.log(payload.hello);
    });
    
    this.state.set('HELLO_WORLD', { hello: 'Hello' });
  }

  ngOnInit() {
    const hello = this.state.get('HELLO_WORLD');
    console.log(hello.hello);
    
    this.state.set('HELLO_WORLD', { hello: 'World' });
    
    setTimeout(() => {
      this.state.set('HELLO_WORLD', { hello: 'Hello World' });
    }, 100);
  }
}
```
