## Install

```sh
yarn create hyperdom-app --jsx myapp # or npx create-hyperdom-app --jsx myapp
cd myapp
yarn install
```

Run dev server:

```sh
yarn dev
```

Open `http://localhost:5000`

## Hyperdom App

An object with a `render()` method is a valid hyperdom component (we call top level component an app). The one in your project looks like this:

<!-- tabs:start -->

#### ** Javascript **

_./browser/app.jsx_

```jsx
const hyperdom = require("hyperdom");
const {hello} = require("./styles.css");

module.exports = class App {
  render () {
    return <h1 class={hello}>Hello from Hyperdom!</h1>
  }
}
```

It's mounted into the DOM in _./browser/index.js_:

```js
const hyperdom = require("hyperdom");
const App = require("./app");

hyperdom.append(document.body, new App());
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKAdAIwIZplATgYyVHwHsA7AFxkqRGAB0yACJ-kAB13hgrjcSYBtRixZtqANzYAaEaLYALAJ7sYuACYkAtmzkBdRgF8Qh6SAhl1MAB4oFFLVCIhSlahVoAeAIQARAPIAwgAqAJoACgCiTPaOAHyMnrFQCcxMSTAY6qmi6RQQFLBx4RgEOEwAyhiWaCTWngD0-YUwOaKeWjwYTPgKpXA8ALxsAKrBAGIAtAAcbEwNbY0KmdmMcp616kptLJ7qEBJMEOrDIBjs7GxxjfsSqXK7cPi4EOwUTHAEp5_4DWi4JAA7gNcA0LFZbAArPgga4NJ4vN6LP4kLapJYOFKMExmdgYfAAawwAHMYChoeRnK4qDREHQ5GwyBhOvxWCBlKoNNpJqSKJM4BRSlR1JMLAUZAyQBI1HAIORWWwAIwoAAMqolaTYVgRr3y8qQbIAEio1JotExfDAtCQmAApCoasQgLQYCwK8yWGx2TGOtk6t4wgQMNJOgVC914spQI6e2zJJiTSYkVRkX1OtAAV2g6gjpXw5Uz2ZjEO9jl0aVMkqsKasZHwEHgrODuTYmGwUEmnG4fI5pu07qgGCoArTbN7XJ0BrYg-HFHLLErmpAVgklpr1HrjYNzfkHDzOEmmcssFwA6H8DnIDki6dBJgSkBJA0gaEBjIhmxphAPz-AOBagac52HJOBrCpcgaQ8OlXAFGITQnJhBiYLgAEcsy4AAKRR4LNNgAEoAG5GBg95gGWKAoBIQxEOQmA0IgTC2BQeEKCUWA4BQfA4BhQi1jIa11AzWAUBsdgn14Gj8EHbimAAQQuJgdy4T1cCYDC8MUh5aIoDNcGYJJFR6aS4EGMicEoww4kNcybTAAFzWNTkzW8JZFTaD930_Mwf3-IEQTBWMQPAtxaRcchYPHM0aNQ9CYCw9kcP7EBeLrcL3nk9horo2L4uYoD8KI1MyEi7QUCA6h1AwzR8AzTpKHQVElGkJgyBgQE5IudSUpxb8CF_PyAIFNj4E47jgsg2hEGJSjMCgDDNiUDSdzACDJjAZloCUAQ2GsqBpXyfBugAORgDMYBkOSXgwKBmrgao4H5NQIDAQqPMYOwbM0tIqGsPkKFwe6VtwLQBAzC41EOgZXs_QxDCAA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

#### ** Typescript **

_./browser/app.tsx_

```tsx
import * as hyperdom from "hyperdom";
import { hello } from "./styles.css";

export default class App extends hyperdom.RenderComponent {
  render() {
    return <h1 className={hello}>Hello from Hyperdom!</h1>;
  }
}
```

It's mounted into the DOM in _./browser/index.js_:

```ts
import * as hyperdom from "hyperdom";
import App from "./app";

hyperdom.append(document.body, new App());
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKA5lA9gIwIZQHQAmeALgsiAMboB2xMtSIBMFU2ATjAAQC26BAV1hcAOiABUeCnDhiR1EAF8ANCAjVmADzwALYjyhJQVWvWKMAPHoMA-efKsxsBO9RHELxCMVg2AChwUMFBcAMrYGpjomhYA9F4-MK7uFjwwxNhcFDoccOkAvGIAqgAqAGIAtAAcYlyxrnE6Ti721BZRBACeyR4EEABuXBAEhSDYAA7jYjZxff3Jbh5wFOwQ48RccOwUo1sUsZjs6ADueeyx6loksiAzscur6w0H_N2tjfpQrkqq49gUAGtsCgYHgAFZwGhGSg0OgMRAgYDyLiiEDUbBpMSIVEg4gVOAZdh0AgVdTeCqkMTKZGo_owdhwCA0LGogCMeAADJyqTSxMwHmsvMykKiedQUWIeNh1CyxJcYNprFAxRKQAL1jdsUjxSjUQSOMRZSA_ttgkMNArdJ8uBUKuhxvQVbqxJgBNACEaTUEQq73earkq5DqVLymDAHRbqBQIPAWdrdaidJ0HewCOgeEauQAmdkcp2q4jJ-ArQVGgDMeAArHhWUGUSGdXyYP0ACLh-jMKMxzVcePO42BYIVV0aWDsI1sOgEutcBuqgEwTrHdCpnsAbQAuvJFD81dsDkdTvTYhNxtdNNCTHDzAiIDxxiuNuIuNg4Fwkym0zwuGAjt-xB-9JfmIADc8h3g-RK9u-wQYLOP5_qieD3IWsBwFIMiga0CqQRszBgNgQgbKwr5vgAgpMXAKnCBBvoBqbpngABKHb0gAwumD7UGYvY0pwFrsAAFAAlLxOoopwxACOw4pWKyWRsDIAByGIwPkwBNFAGCKDYAASsHoAh6ZcLpRYMTwACEjSsjYYHBtu8i7nsB4nGcFwWtopCXrCZiMBBj5cM-r7vmZX5Gf-ID0cBIB2f5UEUeM4VISekxYW41BRYxp4doJaYUAIaS0HgHSdMoXDcccXAJSJwl2U5-6HK5x4Ep0aEYWQxg-fCSBoFguCCSVol9mAsIVARPDQJ02JiPpUB0l4FCZEpMACDAVJVasuBlXAERwPi9IQGAdmKK0ugGWJKJ0JoeLEOwu0jewPDYgIkz0oteTHY5KggKQJiQCg4KQgo5BXr5CJ9mIVD3tA9IAPLrEy1A9n2qqQtJQQALITCyt2rdS4molAECYCya5iPAABs618umYgbvjCZiBCmhGpw_yGiADP9szZTsyunRGplPCAyznM0qjt0QBQHPYrjMBc6qRzoMQLYQOOIpiHsM4ndQOtKIoihAA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

<!-- tabs:end -->

## State Management

It's rare to have to think about state management in Hyperdom. Just like React app, a Hyperdom app is often composed of multiple components. Unlike React though, Hyperdom does not _recreate_ them on each render - your app has total control over how long those components live. Another crucial difference is that Hyperdom always re-renders the whole app, no matter which component triggered an update.

This means you can use normal JavaScript objects to store state and simply refer to those objects in jsx.

## Events and Bindings

Hyperdom rerenders immediately after each UI event your app handles. There are two ways of handling UI events in hyperdom, event handlers (for things like mouse clicks) and input bindings (for things like text boxes).

## Event Handlers

Event handlers run some code when a user clicks on something. Let's modify our `App` class:

<!-- tabs:start -->

#### ** Javascript **

_./browser/app.jsx_

```jsx
module.exports = class App {
  renderHeader() {
    if (!this.hideGreeting) {
      return <div>
        <h1 class={hello}>Hello from Hyperdom!</h1>
        <a href='#' onclick={() => this.hideGreeting = true}>Next</a>
      </div>
    } else {
      return <p>Now then...</p>
    }
  }

  render () {
    return <main>
      {this.renderHeader()}
    </main>
  }
}
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKAdAIwIZplATgYyVHwHsA7AFxkqRGAB0yACJ-kAB13hgrjcSYBtRixZtqANzYAaEaLYALAJ7sYuACYkAtmzkBdRgF8Qh6SAhl1MAB4oFFLVCIhSlahVoAeAIQARAPIAwgAqAJoACgCiTPaOAHyMnrFQCcxMSTAY6qmi6RQQFLBx4RgEOEwAyhiWaCTWngD0-YUwOaKeWjwYTPgKpXA8ALxsAKrBAGIAtAAcbEwNbY0KmdmMcp616kptLJ7qEBJMEOrDIBjs7GxxjfsSqXK7cPi4EOwUTHAEp5_4DWi4JAA7gNcA0LFZbAArPgga4NJ4vN6LP4kLapJYOFKMExmdgYfAAawwAHMYChoeRnK4qDREHQ5GwyBhOvxWCBlKoNNpJqSKJM4BRSlR1JMYBJ3DDZGk2OLcHAIORWWwAIwoAAM6pkDJAVgRr3yiqQbIAEio1JotExfDAtCQmAApCpa6UgLQYCxK8yWGx2THOsQgPVvGECBhpAMCoWevFlKBHb22ZJMSaTEiqMj--QgNAAV2g6mjpXw5Vz-fjEN9jl0aVM2qs6asZHwEHgrLDuTYmGwUEmnG4fI55u0nqgGCoAszAcHXJ0RrYo_HFGrLFrLqsEmtDeozdbRvbWZjxZ7ucssFwI7H8CXIDkq4DBJgSkBJA0IaEBjIhmxpkDBD-AOBNQGnOdhyTgawqXIGkPDpVwBRiM0ZyYQYmC4ABHPMuAACkURCLTYABKABuRg4PeYBligKASEMZDUJgDCIGwtgUHhCglFgOAUHwOAYWItYyFtdQc1gFAbHYF9eDo_BR14pgAEELiYfcuG9XBjRWNQsII5SHiOMAmCw7wKAUCAuNMqwAHEuB4CxiR0_dci4Cgc1wZg9gOHZcnSBRlR6WS4EGCicGoww4g0qi7TAAFLVNTkLW8JZlS83JPG6BQuDAQYAHIAGJsqYcgZIgQkgu05C4iYEyzLsY4YGsmBbLIYk6IoXAcxgMKADkbAoRoMBS9IGluLzaJwAZdPDURnNc9z2DiLqgSq5YyBQNbGnmvSvxrASWFUqxcEMhy9Jmtz0jdCxBuAaquP2tQNKyLSCO21KGgusg2m27acV_X5_iBEEwQTMDILcWkXHIeDpwtOj0MwmAcPZPDhxAfim0h95FPYWGGPhxHWJAwiSIzMhoe0FAQOodQsM0fAc06Sh0FRJRpCYMgYEBBSLm0tGfp-f8AaAgUOPgbjeNB6DaEQYlqMwKAsM2JRjrSMAoMmMBmWgJQBDYCLxXyfBuh6jqZAUl4MCgVm4GqOB-TUCAwGJ7bGDsEK7X3KhrD5NqbdV3AtAEHMLjUQ2Bid79DEMIA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

#### ** Typescript **

_./browser/app.tsx_

```tsx
export default class App extends hyperdom.RenderComponent {
  private hideGreeting: boolean;

  renderHeader() {
    if (!this.hideGreeting) {
      return (
        <div>
          <h1 className={hello}>Hello from Hyperdom!</h1>
          <a href="#" onclick={() => this.hideGreeting = true}>Next</a>
        </div>
      );
    } else {
      return <p>Now then...</p>;
    }
  }

  render() {
    return <main>{this.renderHeader()}</main>;
  }
}
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKA5lA9gIwIZQHQAmeALgsiAMboB2xMtSIBMFU2ATjAAQC26BAV1hcAOiABUeCnDhiR1EAF8ANCAjVmADzwALYjyhJQVWvWKMAPHoMA-efKsxsBO9RHELxCMVg2AChwUMFBcAMrYGpjomhYA9F4-MK7uFjwwxNhcFDoccOkAvGIAqgAqAGIAtAAcYlyxrnE6Ti721BZRBACeyR4EEABuXBAEhSDYAA7jYjZxff3Jbh5wFOwQ48RccOwUo1sUsZjs6ADueeyx6loksiAzscur6w0H_N2tjfpQrkqq49gUAGtsCgYHgAFZwGhGSg0OgMRAgYDyLiiEDUbBpMSIVEg4gVOAZdh0AgVGD9MxwCqkMTKZGo8nsOAQGhY1EARjwAAYuTS6WJmA81l4WUhUbzqCixDxsOpWWJLjBtNYoOLJSBBesbtikRKUaiCRxiHKQH9tsEhhpFbpPlwKhV0ON6Kq9WJMAJoARjaagiE3R6LVdlXJdSo-UwYI7LdQKBB4KydXrUTpOo72AR0DxjdyAEwcznOtXEFPwFZC40AZjwAFY8GzgyjQ7r-WSACIR-jMaOxrVcBMuk2BYIVN0aWDsY1sOgE-tcRtqgEwTrHdBpnsAbQAuvJFD91dsDkdTjBzhNxtdNNCTHDzAiIDxxiuNuIuNg4Fxk6n0zwuGAjt-xB-x5fmIADc8h3g-RK9u-wQYLOP5_qieD3EWsBwFIMiga0iqQRszBgNgQgbKwr5vgAgpMXCKnCBBvoBaYZngABKHbHgAwhmD7UGYvZ0uMqz9NgdDvsMMAAOKcOk6goNiUToLAERgW4uqcJa7AABLNMeAAUACUvG6iiEBgFw2kAITEDoEDoVZzASTAUnUCg-l9omnDEAI7AStpdKJiiFhzK4fl-VYbJZGwMgAHIYjA-TAE0UAYIoNiaYl6AIRmXDqcWDE8GZjRskFwV6hYmQ6JwYCjAAxLUNCsBAgJxXpXD5DYXCWdZuiifZjkoC17XsAIMDJZF1FxNgRXBbMAyTXqulKYmihUVAeQGcF7meRKFjjDYkUnO1TTUHgx1xDtC16oodKXcpKKqcw7DNa5XAbV5XCpDK1A2MAHXoXdx6ac4Om6YocTSuoNjndd127nsB4nGcFyWtopCXrCZiMBBj5cM-r7vjlX4Zf-ID0cBIBKZjUEUeMhNIbEp5YcpJOMaeHbaemFACGktB4B0nTKFw3HHFwVN6fN8gw_uhzw8eKGdGhGFkMYaPwkgaBYLg2m8y5dJgLCFQETw0CdNiYipeSXgUJko1DTSwurLg_NwBElJnMZSnXfIuiwelfZ0JoeLEOwzu6-wPDYgIkzHpbeTu-LKggKQJiQCg4KQgo5BXujCJ9mIVD3tAx4APLrMy1A9k9YiQp5QQALITKygdDbShmolAECYKya5iPAABstv8hmYgbs3iZiBCmjGpw_xGiAI_9uPZTTyunTGkzPCpxPs--fqgcNTP2KNzAc9qkc6DEC2EDjqKlfbDOUNx4oihAA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

<!-- tabs:end -->

When "Next" link is clicked, the `onclick` handler is executed. After that, hyperdom re-renders (that is, calls the `render()` method, compares the result with the current DOM and updates it if needed).

Read more about Events [here](api#event-handler-on-attributes)

## Input Bindings

This is how we bind html inputs onto the state. Let's see it in action:

<!-- tabs:start -->

#### ** Javascript **

_./browser/app.jsx_

```jsx

  renderBody() {
    if (this.hideGreeting) {
      return <div>
        <label>
          What is your name? <input type="text" binding="this.userName"></input>
        </label>
        {this.userName && <div>You're now a <strong>hyperdomsta</strong> {this.userName}</div>}
      </div>
    }
  }

  render() {
    return <main>
      {this.renderHeader()}
      {this.renderBody()}
    </main>
  }
}
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKAdAIwIZplATgYyVHwHsA7AFxkqRGAB0yACJ-kAB13hgrjcSYBtRixZtqANzYAaEaLYALAJ7sYuACYkAtmzkBdRgF8Qh6SAhl1MAB4oFFLVCIhSlahVoAeAIQARAPIAwgAqAJoACgCiTPaOAHyMnrFQCcxMSTAY6qmi6RQQFLBx4RgEOEwAyhiWaCTWngD0-YUwOaKeWjwYTPgKpXA8ALxsAKrBAGIAtAAcbEwNbY0KmdmMcp616kptLJ7qEBJMEOrDIBjs7GxxjfsSqXK7cPi4EOwUTHAEp5_4DWi4JAA7gNcA0LFZbAArPgga4NJ4vN6LP4kLapJYOFKMExmdgYfAAawwAHMYChoeRnK4qDREHQ5GwyBhOvxWCBlKoNNpJqSKJM4BRSlR1JM0OCLMSYbI0mwJGo4BByKy2ABGFAABg1MgZICsCNe-SVSDZAAkVGpNFomL4YFoSEwAFIVbUykBaDAWZXmSw2OyYl1iED6t4wgQMNKBgVCr14spQI4-2zJJiTSYkVRkAPyEBoACu0HUMdK-HKeYLCYhfscujSph1VgzVjI-Ag8FZ4dybEw2Cgk043D5HIt2i9UAwVAFWcDQ65OmNbDHE4oNZYdddVgkNsb1BbbeNHezsZLvbzllguFH4_gy5AcjXgYJMCUgJIGlDQgMZEM2NMQYIfwBYE1Aac52HJOBrCpcgaQ8OlXAFGJzVnJhBiYLgAEd8y4AAKRQkMtNgAEoAG5GHg95gGWKAoBIQwULQmBMIgHC2BQeEKCUWA4BQfA4BhEi1jIO11FzWAUBsdhX14ej8DHPimAAQQuJgDy4H1cBNFY1GwwiVIeI4wCYbDvAoBQIG4syrAAcS4HgJV0g9ci4Chc1wZg9gOHZcnSBQVR6OS4EGSicBoww4k06j7TAAErTNTlLW8JYVS83JPG6BQuDAQYAHIAGJsqYchZIgQkgp0lC4iYUzzLsY4YBsmA7LIYl6IoXBcxgMKADkbAoRoMBS9IGluLzv1rQSWDUqxcAAIVRJRyscgyjOqiy6oapriQc_TJp4Vz3JGnb2jHHtBtyAB1Pp3nMpglBIVymCZToAH50gsdhc3eDjVFOKhrBvJgxUsCVfrM7jcxBLrmRgK5Gnez6zqGk6cER4BVpQCG1ChzomAAMlx9IRtCe7sq4R6gSYbpPAFAFmriGdLSjRoafIYlKrRsGMch6HDBuTyxu8obDojJgBdFiaGPUxb9Oc_b0ndCxBo5mqprUTSsm0wixdyZXuNV2b5p07WhoVsg2jGsacT_X5_iBEEwUTcCoLcWkXHIBCGe0eiMKwmBcPZfCRxAATm3d94lPYb3GN9_22NAojSMzMhPa0FBQOodRsM0fBc06Sh0Hm6RHpgQFFIuHSQ6tn4ALt4CBU4-AeL452YNoRBiRozAoGwzYlG2tIwGgyYwGZaAlAENgIrlfJ8G6HqOpkRSXgwKAi7gao4H5NQIDAROxsYOwQvtA8_r5NqN8H3AtAEXMLjUWeBj3wT0Ea3AABlzIouRag0NRJlIai5wBgCAAWOdgj8jDP2wGoD-CE2p6TSD_aaooSAUAoNoAQKp2DWA-CQKAxwmD4OJPYYkXAlBPyTi_GBn8qrqGlFQ9-NDTIIJYHidQ-xmqYPVNgihJhDCGCAA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

#### ** Typescript **

  _./browser/app.tsx_

```tsx
  renderBody() {
    if (this.hideGreeting) {
      return (
        <div>
          <label>What is your name? <input type="text" binding={[this, "userName"]} /></label>
          {this.userName && <div>You're now a <strong>hyperdomsta</strong> {this.userName}</div>}
        </div>
      );
    }
  }

  render() {
    return (
      <main>
        {this.renderHeader()}
        {this.renderBody()}
      </main>
    );
  }
}

```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKA5lA9gIwIZQHQAmeALgsiAMboB2xMtSIBMFU2ATjAAQC26BAV1hcAOiABUeCnDhiR1EAF8ANCAjVmADzwALYjyhJQVWvWKMAPHoMA-efKsxsBO9RHELxCMVg2AChwUMFBcAMrYGpjomhYA9F4-MK7uFjwwxNhcFDoccOkAvGIAqgAqAGIAtAAcYlyxrnE6Ti721BZRBACeyR4EEABuXBAEhSDYAA7jYjZxff3Jbh5wFOwQ48RccOwUo1sUsZjs6ADueeyx6loksiAzscur6w0H_N2tjfpQrkqq49gUAGtsCgYHgAFZwGhGSg0OgMRAgYDyLiiEDUbBpMSIVEg4gVOAZdh0AgVTCXdQoOAVUhiZTI1H9GDsOAQGhY1EARjwAAYebT6WJmA81l42UhUfzqCixDxsOp2WJLjBtNYoJLpSBhesbtikVKUaiCRxiAqQH9tsEhhplbpPlwKhV0ON6OqDWJMAJoARTeagiEPV6rVdVXJ9SoBUwYM7rdQKBB4Oy9QbUTpOs72AR0DxTbyAExc7mujXENPwFYi00AZjwAFY8BzQyjw_rBTB-gARKP0Zix-M6rhJt1mwLBUkCDSwdimth0AmNrjNjUAmCdY7oDP9gDaAF15Ip5D9NdsDkdTkzYhNxtdNNCTHDzAiIDxxuuNuIuNg4FxU-nMzwuGARz_mIP5Mn-YgANzyE-L5EgO37BBgC4AUBqJ4PcJawHAUgyJBrTKrBGzMGA2BCBsrCfl-ACCkxcMqcIEF-oEZlmeAAErdkyADCWYvtQZgDvS4yrP02B0N-wwwAA4pw6QUtiUToLAERQfqwkDGJ3ACGcAByGIwNiBKrNQKCqfSnDWuwAASzRMgAFAAlIJ-oohAYBcHZACExA6BA2G-cwMkwHJJlOYOyacMQAjsFKdn0smKIWHMrgJQlVgclkbAyHpaT5MATRQBgig2DZhXoChWZcFZpYsTwnmNByKWpQaFiZDonBgKMADEtQ0KwECAnljlcPkNhcD5fm6JJQUhSgI3jewAgwMVOn0XE2BNalswDJtBoOapyb7mGrQohZzDsAAQq8w3hUM7l2RN_nTbJXihc5qWRdFsXxWlyU_VtbCYMENgAOo5BsflcJ06DRVw6JpAA_FwFjqOMAgbCWzqjHQmgmiAXBkhoFJ5Zuj3KKi2lMjlMBiNuih1HcgPA_9CXAI9eCU-w1NcAAZDzyPJQAmjDADknBwycH7I0ZNAoDYzF_kacQyyZY1s752Gc9TijbfMR3NcjsR_S5e0HQa-sLidXBnfZYU_Z9MUeSzqRytQu3Jurk029ZtnsI5FupZ72He1dXT-87sSyuou37fSR1HQeKhHvshwnGcFzWtopC3rCZiMDBr5cO-n7fjVf4VcBIAK1meHUAXcE0eMFdoReky1_I1c8Hgl7dnZmYUAIaS0HgHSdOT_HHFwjeObHChJ3sJ5p-eBKdFhOFkMYufwkgaBYLgdmj3b-pgLCFQkTw0CdNiYilYyXgUJkq1LbSU-rLg5NwBEVJnG5qkJ9QuhELlUHDjPExB2BfxPuwHg2IBCTCZA_PIf9E6qFICYSAKBwSQgUOQO8ecESDjEFQZ80AmQAHl1ismoP2W6YhITRSCAAWQmOycBS06QmzEFACAmB2SbjEPAAAbC_QUNcQDbg4cmMQEJNCmk4P8PGkihwyLKAo9cnRTSdywbIkASiNRGQGnjbEbCYB6NREcdAxB2wQCnOKOh2x5zx0TooRQQA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

<!-- tabs:end -->

Each time user types into the input, hyperdom re-renders.

Read more about Bindings [here](api#the-binding-attribute)

## Calling Ajax

The above examples represent _synchronous_ state change. Where it gets interesting though is how much trouble it would be to keep the page in sync with the _asynchronous_ changes. Calling an http endpoint is a prime example. Let's make one:

<!-- tabs:start -->

#### ** Javascript **

_./browser/app.jsx_

```jsx

  renderBody() {
    return (
      <div>
        <label>
          What is your name? <input type="text" binding="this.userName"></input>
        </label>
        {
          this.userName &&
            <div>
              <div>You're now a <strong>hyperdomsta</strong> {this.userName}</div>
              <button onclick={() => this.getBeers()} disabled={this.isLoadingBeer}>
                Have a beer
              </button>
            </div>
        }
        {this.isLoadingBeer ? "Loading..." : this.renderBeerList()}
      </div>
    );
  }

  renderBeerList() {
    if (!this.beers) {
      return;
    }

    return (
      <table class={styles.beerList}>
        <thead>
          <tr>
            <th />
            <th>Name</th>
            <th>Tagline</th>
          </tr>
        </thead>
        <tbody>
          {this.beers.map(({ name, tagline, image_url }) => {
            return (
              <tr>
                <td>
                  <img height="50" src={image_url} />
                </td>
                <td>{name}</td>
                <td>{tagline}</td>
              </tr>
            );
          })}
        </tbody>
      </table>
    );
  }

  async getBeers() {
    delete this.beers;
    this.isLoadingBeer = true;

    const response = await fetch("https://api.punkapi.com/v2/beers");
    this.beers = await response.json();

    this.isLoadingBeer = false;
  }

  render() {
    return (
      <main>{this.hideGreeting ? this.renderBody() : this.renderHeader()}</main>
    );
  }
}
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKAdAIwIZplATgYyVHwHsA7AFxkqRGAB0yACJ-kAB13hgrjcSYBtRixZtqANzYAaEaLYALAJ7sYuACYkAtmzkBdWc1YcoAVwDmEMnyRC5YkBVwZrYEri0BaXKcoQtMLpGeowAvowgodIgVuowAB4oChRaUEQgpJTUFLQAPACEACIA8gDCACoAmgAKAKJMyakAfIy5jVAtRm0wGOqdoky5FBAUsE3VGAQ4TADKLupoJPG5APTDozD9orkBFBhM-AqTcDwAvGwAquUAYp4AHGxMK1urCj19jHK5i-pKWyy5dQQCRMCDqc4gDDsdhsJqrIESTr2QZwfC4CDsChMOAECE4_ArNC4EgAdxOuBWsQSKAAVjY4StUejMS9CSRfp1XikOhEohwMPgANYYcwwWlwcjpTJUGiIOhyNhkDABfjGZSqDTaTyiiieOB7XBUdSeDA0jDxGQKkASNRwCDkVVsACMKAADG7LUY2HEmRjhg7bGwABIqNSaLRMQowLQkJgAKRmnocWgwVkdMTIcUS7STxl9mJsAgYRgc-smFHT7Em-GmVOz3KYnk8JFUZFzDjQpmg6kr1emne7oMz1JzIDkUStcVbcTI-Ag8FVxYGbEw2CgnnYZksZE8ThccDcHm8vmGKsDICgGCo-vbxlXOA3XBOuvVYe06cv14rIEMy5Ar81HRz0_eBv3HX9jDiCQo2nag5wXWwl3kfkpnXTtM1gXAPyvUCghYCcvRAQUYCUEl3HUQshBCMhwjISJonxQliTJNQVihdhxXiKVyBlHI5UyfUGlDQCmFOJguAARy7LgAApFGE8M2AASgAbkYASsX1JRYDgUTxJgKSIFktgUEZChtPgFB8DgGxVM-MgY3UUxYBQBJ2HcXg9PwS8bKYABBaEmCQrhh1wIN3jUGSlKC5EuAoUxcGYOSS22BF_gGQYFCdA4fLgU5gC0nSkhwKASFCJpwqgUqmDAYkIxDDVw3yV4nXSgZcn2BQuDACEAGJHnIbyICFfKotEpomBkigFAgOAkjBGAAHEuB4KxzD0pxTBgJTyuRDKmAAOQSCsUvati2sGFY0uROyjFouQQriXAACF2SUMakJYOKEqSvbBmu07tkvNcLoGAB1I4sVmpglBIBKmCVAIAH5BisdhTCxczVAhKh4m_Jg0FiNacZmubTHJA7lUCEAGTRjHQcu4GcAZz79qYabZpQcm1EpgImAAMn5v79sBYEGZFtLKjhgByLgEdJJh9lyfViTIcwmgA8My1WFXyHVoKObJimqdCeExeFtnvgxihyCYQaoGGwVRui04JsNlAdWemBbSi0ImCBOAsFgcFgHd2aABkSF6NavbUXbAbZ0QgwwG1FYJ72sITy3CWt8hxe2K7zaz2jE9D0mUAjqOgTV2PcCYFG2Ej6O1ZQVvHgEd3HrUWvw9mihfb-s3ERutS7vsr7qCenu-4-5EIDASb8nd7BbWi1mJ_ixLR4Ge6Uu-xLJsHvY0FgHKMBs_LCsslfcF7_V48ToY3l6fOhlwfOAWmp4P8Gaaml5mAqw_4W3an_coIoHZkEAWsBQr81jvwtkA5-Hws5DB-H8EBBty43zmimdgMkZLAARlTaQ7MIFWBgKQ_wIoYAAH0EpQCYKEF2E115s33r9LOIsnA_1ASgxOAjUZaHWm8CA5hkgQgAKyukePifK1DRT0NwFAP2zxMEizWPwwRGUhh9GAIjGAptNG8O2BQPRexzCQMMUArR2jLo8PUUwW6gjmEl2zhQdBF0gFB02CPcc49FZwCULOJgnsM5wFnilOIsAqDs2weE7eogw5wCbtXcwtcNo-BgKPZEGl9JwHctYGAekMAklTFiMAPBDhyX_BQCg7A4CIBWGxdgEAUDozIMKVpVltArAkAAJkJOE5SiSWDL3CSUspIx8mFJOOKcgUUckpWSakmOGc9JgAwFAE4iTd4T1CpEgYHDD6Ax2KmMgTQy6cxmnEZa3thhq3rnEzmXcXpvTGh3curzwq9EijtVYKYrDpWcUwsIvIGIECYqScklJhyJDpNxLIsoMjkEEprbQelJLSRgDU9FQFbp5ICuwTFBlsU1NMuxEZ9k8UoHYpPGSmh8CmACJQdAb1SFQJJP5aEUVbr0RAIxIk0LWJXzmtZBAyAUVIr4kgSxJBMBQBkugtecg3CUE8JsrQ0AlACGDDgG0wx8D7COltGQ_l0RbNIYHaweo1Dz1HrvYqVVYxIVxrqPcrh3BaAEKYaEagjU7LBW2Mg6AM53yxEhRYGg1CeFIFVKEJwBBxsvA07JQbGChrUOG9mddI3kRjYsOp2gBBOnYPEbEJAHbqCYA7cRFBzBcCUA6-ymbb593ZuoQwrbs1fyQlWdQaSS2ujLc2uioRx1AA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

#### ** Typescript **

_./browser/app.tsx_

```tsx
  renderBody() {
    return (
      <div>
        <label>
          What is your name? <input type="text" binding={[this, "userName"]} />
        </label>
        {this.userName && (
          <div>
            <div>
              You're now a <strong>hyperdomsta</strong> {this.userName}
            </div>
            <button onclick={() => this.getBeers()} disabled={this.isLoadingBeer}>
              Have a beer
            </button>
          </div>
        )}
        {this.isLoadingBeer ? "Loading..." : this.renderBeerList()}
      </div>
    );
  }

  renderBeerList() {
    if (!this.beers.length) {
      return;
    }

    return (
      <table className={styles.beerList}>
        <thead>
          <tr>
            <th />
            <th>Name</th>
            <th>Tagline</th>
          </tr>
        </thead>
        <tbody>
          {this.beers.map(({ name, tagline, image_url }) => {
            return (
              <tr>
                <td><img height={50} src={image_url} /></td>
                <td>{name}</td>
                <td>{tagline}</td>
              </tr>
            );
          })}
        </tbody>
      </table>
    );
  }

  async getBeers() {
    this.isLoadingBeer = true;

    const response = await fetch("https://api.punkapi.com/v2/beers");
    this.beers = await response.json();

    this.isLoadingBeer = false;
  }

  render() {
    return (
      <main>{this.hideGreeting ? this.renderBody() : this.renderHeader()}</main>
    );
  }
}
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKA5lA9gIwIZQHQAmeALgsiAMboB2xMtSIBMFU2ATjAAQC26BAV1hcAOiABUeCnDhiR1EAF8ANCAjVmADzwALYjyhJQVWvWKMAPHoMA-efKsxsBO9RHELxCMVg2AChwUMFBcAMrYGpjomhYA9F4-MK7uFjwwxNhcFDoccOkAvGIAqgAqAGIAtAAcYlyxrnE6Ti721BZRBACeyR4EEABuXBAEhSDYAA7jYjZxff3Jbh5wFOwQ48RccOwUo1sUsZjs6ADueeyx6loksiAzscur6w0H_N2tjfpQrkqq49gUAGtsCgYHgAFZwGhGSg0OgMRAgYDyLiiEDUbBpMSIVEg4gVOAZdh0AgVbBg7CaCqkMTKZGo_owdhwCA0LGogCMeAADNyaXSxMwHmsvKykKi-dQUWIeNh1GyxJcYNprFAJVKQEL1jdsUjJSjUQSOMR5SA_ttgkMNErdJ8uBUKuhxvQ1fqxJgBNACCazUEQu7PZariq5HqVPymDAnVbqBQIPA2br9aidJ0newCOgeCaeQAmTlcl3q4ip-ArYUmgDMeAArHh2SGUWG9QKYP0ACKR-jMGNx7VcROu02BYIVd0aWDsE1sOgEhtcJvqgEwTrHdDpvsAbQAuvJFD8NdsDkdTozYhNxtdNNCTHDzAiIDxxmuNuIuNg4FwU2mMzwuGAjr-YhfoyP5iAA3PID5PkSXCvu-mzFrAH7_pmqJ4PciHwFIMjga06h0OwYD_NwABCMCMv2dLomk2IEqs1AoBBeoZGg6gwLRxD0YxdIPsCMAAPoCOwUAcVxTGKK0SrQRszBEUIGysO-H4AIKTFwSpwgQH7AemmZ4AASl2jIAMKZk-1BmJRerjKs_TYHQn7DDAADinDpOoKBcPkf64HkTEojZAz2dwAhnAAchi3DeXIID-VwgV2Q5EBwAAMugzgeWRFHeURUB-XSCXBVwmDkUy2LKew7DYJ0FhZewNheVw25MXSnBWuwAASzSMgAFAAlFZSacMQQmSj1dJJhYcyuEmk06OyWRsDIEVpPkwAEp0SG6MEGCKDYXVQBgf4AVwHUlrpPAAISNOyM2zSiFiZDonBgKMADEtQ0KwECAmt_VeQ1PXEDoyW6E5rnkV4DGNZxAgwH1e1hRpcTYHdk2xNNE1cH1cUSW4eptcw7Aka8_0Diiw2jVw416pNmO07NFhsCVXxY_dADqOQbMlXCdOgQlcNRMAAPxcBY6jjAIGzFk6ox0JoxogMVlweWtG7A8lyioqFjIrTAYhboodRo4zsTM8EJtJsAGtwHgOvsHrXAAGRO9TbOM_T933VNAyW17KIAJr8wA5JwgsnG-Yt0TQKA2DpP6GnE0cMQ11sg7b9t63j_vo57OcPe6xDEDQXBfVAP0An9A35A1Nt4LidVwP1Rt9HA2CYLAIxp6DyVpRlDF1Xt7v-x12AMpHJWMsPpuF8X1B-7nvvTwj0_d7bvfpX0A-lVwotiH3W8oHgx-1NideE4ydUpclxDN-7sxLwzON0njrVGcTpXXwSZNYxAYDU5dOuk8mR4FgAxYGA1yb6kpuwagcVGytCGukKmNNvYZA7twRSy1IprQ2ltYBX9iBDwZpNYGzQF76k8PVaepCdDGxoZQ4GNg9ZxCYQwh6TCSjAnLhZVhOgKEPXiNQkhlD4hNGcBQzwHQ3giKtkA0qtsZTjB6j1YAgtIpaxYjwmAWteIgkEsJec1dU7sK4DAsapiOHCPzmglw4seCeSaBAFAeg1rVi5EbPYa09ECSElAI29RWEtFkTnTwLhgBC0UEEgRXswk2GttwtiUT4jBJsaIziMSUTPxCY2FeITWHSL9qw9uvgsbZIQfjFE75Ogxi4A3BRP8GZ1w3v3FAdUYbsDhi1BmJgCRmPgOZPIjVsDHFlBsMA6RsjjRAHoYg4w4CIFiGecYEA8CS2oECFZUhMyxH6DmA4CixDlP1PIxkH5vIjLGf0uAgzQQQhoP1bpSZmmpU3plHeOVfIwFxog_p7VGlIJGrAt2IjUiynnmvMGzAIbuWhqLc-78SZdH-mfdOeAL6dW6uwZucQZTqBNscvGeN9x7CPCcM4FwrTaFINeWEZhGBQWfLBN82lzo_mOqhICbLMy4WoIymCqlxgcsAiAdC55eXyHjnpc8XYeoZgoAINItA8DSK1hZY4XBBX9WySSw8hxyWnjwVhaQZBjB0vhEgNAWBcA9WkZAukYBYQVCIjwaAnRsRiAOgyLwFBMhIzhjSTVqxcBazbtQOA-JGR_3Eq0bah10CDS4PLPEnEIhwEdewHg2IBCTEZL6_K1BX7UBVZ_G-iaojpkZBUKgh0Jh5GxDWtg8zvm7ljQQstnFy1riJqOdARdMzYnZOMTQmx0DlwIFwcuLjiAoE4J0GN-MS2MkIUmggtJi3tr6cDRNfwCCH0HVyYdC79ykBMJAI-9yFDkBvPShEA4xBUEfNARkAB5dYLJw0JixmISEQkggAFkJhslhjo79IBy6YDZBuMQ8AABsgaBQ8pAFuddSYxAQk0CaTg_xFaocHBhsoOG1ydBNFKng4I4CYZAHh9UdEfqKzPp00DDMxBHD7W2CAk4xQ_u2HOIl8glCKEUEAA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

<!-- tabs:end -->

When "Have a beer" button is clicked hyperdom executes the `onclick` handler and re-renders - just like in the "Events" example above. Unlike that previous example though, hyperdom spots that the handler returned a promise and schedules _another_ render to be executed when that promise resolves/rejects.

Note how we take advantage of the two renders rule to toggle "Loading...".

## Composing Components

Our `App` class is getting pretty hairy - why not to extact a component out of it? Like that beer table:

<!-- tabs:start -->

#### ** Javascript **

_./browser/BeerList.jsx_

```jsx
module.exports = class BeerList {

  async getBeers() {
    delete this.beers;
    this.isLoadingBeer = true;

    const response = await fetch("https://api.punkapi.com/v2/beers");
    this.beers = await response.json();

    this.isLoadingBeer = false;
  }

  renderTable() {
    if (this.beers) {
      return (
        <div>
          <table class={styles.beerList}>
            <thead>
              <tr>
                <th />
                <th>Name</th>
                <th>Tagline</th>
              </tr>
            </thead>
            <tbody>
              {this.beers.map(({name, tagline, image_url}) => {
                return (
                  <tr>
                    <td>
                      <img height="50" src={image_url} />
                    </td>
                    <td>{name}</td>
                    <td>{tagline}</td>
                  </tr>
                )
              })}
            </tbody>
          </table>
        </div>
      );
    }
  }

  render() {
    if (this.isLoadingBeer) {
      return <div>Loading...</div>
    } else {
      return (
        <div>
          <button onclick={() => this.getBeers()} disabled={this.isLoadingBeer}>Have a beer</button>
          {this.renderTable()}
        </div>
      );
    }
  }
}
```

And use it in the main app:

_./browser/app.jsx_

```jsx
const BeerList = require("./BeerList");

module.exports = class App {
  constructor () {
    this.beerList = new BeerList();
  }

  renderBody() {
    return (
      <div>
        <label>
          What is your name? <input type="text" binding="this.userName" />
        </label>
        {this.userName && (
          <div>
            You're now a <strong>hyperdomsta</strong> {this.userName}
          </div>
        )}
        {this.userName && this.beerList}
      </div>
    );
  }

  renderHeader() {
    return (
      <div>
        <h1 class={styles.hello}>Hello from Hyperdom!</h1>
        <a href="#" onclick={() => (this.hideGreeting = true)}>Next</a>
      </div>
    );
  }

  render() {
    return (
      <main>{this.hideGreeting ? this.renderBody() : this.renderHeader()}</main>
    );
  }
}
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKAdAIwIZplATgYyVHwHsA7AFxkqRGAB0yACJ-kAB13hgrjcSYBtRixZtqANzYAaEaLYALAJ7sYuACYkAtmzkBdWc1YcoAVwDmEMnyRC5YkBVwZrYEri0BaXKcoQtMLpGeowAvowgodIgVuowAB4oChRaUEQgpJTUFLQAPACEACIA8gDCACoAmgAKAKJMyakAfIy5jVAtRm0wGOqdoky5FBAUsE3VGAQ4TADKLupoJPG5APTDozD9orkBFBhM-AqTcDwAvGwAquUAYp4AHGxMK1urCj19jHK5i-pKWyy5dQQCRMCDqc4gDDsdhsJqrIESTr2QZwfC4CDsChMOAECE4_ArNC4EgAdxOuBWsQSKAAVjY4StUejMS9CSRfp1XikOhEohwMPgANYYcwwWlwcjpTJUGiIOhyNhkDABfjGZSqDTaTyiiieOB7XBUdSeUhadgkE4yBUgCRqOAQciqtgARhQAAZ3VajGw4kyMcNHbY2AAJFRqTRaJiFGBaEhMABSMy9Di0GCsTpiZDiiXayeMfsxNgEDCMDn1kwoGfYk3w0ypOe5TE8nhIqjIeYcaFM0HUVZr0y7PdBWepuZAcii1ribbiZHwEHgqpLAzYmGwUE87DMljInicLjgbg83l8wxVQZAUAwVH1HeMa5wm64J116vD2gzV5vlZAhhXIDfTUdAvL94B_Cc_2MOIJGjGdqHnRdbGXeR-SmDcuyzWBcE_a8wKCFhJ29EBBRgJQSXcdQiyEEIyHCMhImifFCWJMk1BWKF2HFeIpXIGUcjlTJ9QaMMgKYU4mC4ABHbsuAACkUESIzYABKABuRhBKxfUlFgOAxIkmBpIgOS2BQRkKB0-AUHwOAbDUjTyCEgAhGA1AAGQgITxKkmSYHkkAzJc9zPJ_ez2zIWN1FMWAUASc1DT08T8CvWymAAQWhJhkM0nx8AodwmFk5SsuRCgFE89BXNwDyvKYMgYBJJgguqkKivUow6LkLgR1wJz2SUIqStLAyKFMXBmHk4aAQRf4BkGK911muamAAdSOLFPKYJQSDGurlRgAB-QYrHYUwsQs1QISoeIfyYNBYiscwrvKuAUFMckADl9seZ5kQGVYFpwJbRGAMqKvetQvoCJgADIYcKv65sBYFgeWyodoAci4OrSSYfZcn1YkyHMJpAIjctVkJ8gSaysHXoh3AoZgOjlv-lYZsRlhlJZ1nQZet7Pv22H4bpyrgv1Hm2Y54awoIz4jG6uJcGDd41EG5CWC4UbxoRqbBml1nBgUZ0DhSuBTmAbTdKSHAoBIUImhVqA7aYMBiUjUMNQjfJXmdVHBn2BQuDACEAGJHnIZKICFC3BtOJpCtF8q4gAcS4HhHv0pxTBgbmmg-hIKFWDBgfhFHkVlphOoV6glfV5EtbGibEZ2NMyCaPmKuTmA09c4ZiaYI7RcVtQ-t-QaBGH2u1BV3o1e51ZUysWbK7ouiGJAJiiVJckVmamqKC4nisllDJHKxMntH0nzjL8hSvY_EAws07ELN06_DN8_yzKtqybLs9qjBIrRTFHFdwvB9LJQwKlfeIUhpyGgUoOcTAdTNTgPXYacRYBUCYKLbAdp2oDFFp5NyJBeiPWalnHwMBAHDRfs-c01gYD6QwCSNMWIwA8EOP5ZIFB2BwEQCsdi7AIAoFOmQYUIjrLaBWBIAATISKqADSr83wbgRKeM2EjAMnARhJxxTkDavLIh_MSFkKBMTSh4kwAYCgCcQhVdjEGR6uULAsAMEDAgGAROqilHFQ1qIRuOtJqG2RoiTm2w9hoFgKbaB5tLZvysmog-DsIn_TKu8f2y0hi4CyazIYCgnh5OyWVfO-1VilLSfk0prjzBQCsDACpChinbDWLkqpAI1hvF6C0oYPw_gdJBngpRKBUzsFkrJYASoAjSFwSKep9VZn-BFDAAA-mNKAoRirxyGobQ2QTm56z2ZE9pRzjmRI-Gc852x_DmAaDACA5hkgQgAKxukePiC2yzRTrNwJsopgzQlrEudc0JFA-hTP2qECpILQUlIhXsOpDToXApadktpaLRDKUBVXbmgyKn9LyRUtxmwIll3CXrSucsOpOJHrgDxogvE-IqmY8hliqr-MRgc_WKNSFsvMCgQV5LZqhCYDgE4uy5rcpCfkg2ezvhnXyswSO9SY7ADjgnUWqClFFVFUCOAJLwSd1eqyix5hmoO2DBgW0eM7pVVWF2CgSq8nGpQHS1x0S_J4rOcKxGVLHE0toryRiBBmI7zYvWcUx8-K0BfpfSM3lP63x4YpR-z9z7pUyomoyJkArCJhE_Wh8aUAcVrrJTQ-BTABEoOgfqsz6qNQyuM5SYUN5bxYrvX-r1_7RuyLQRAdSSCYCgLJfpnKjBuEoJ4GxWhoBKAECGHAtphj4H2AXHOMh0rolsbMg11g9RqC8e1auNtnZxmQtdXU-5XDuC0AIUw0I1CrvsWEeWYsWpCWQosDQagTQkGdlCE4AhSAAf4TQ194V30H1wbgSV36laeEWE67QAhnTsHiNif9YImD1KeRQcwXAlDHrfckuB4LDBQbI4U5C1Z1BmtQ26dDxH6KhFY0AA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

#### ** Typescript **

_./browser/BeerList.tsx_

```tsx
interface Beer {
  name: string;
  tagline: string;
  image_url: string;
}

export default class BeerList extends hyperdom.RenderComponent {
  private isLoadingBeer = false;
  private beers: Array<Beer> = [];

  render() {
    if (this.isLoadingBeer) {
      return <div>Loading...</div>;
    } else {
      return (
        <div>
          <button onclick={() => this.getBeers()} disabled={this.isLoadingBeer}>
            Have a beer
          </button>
          {this.renderTable()}
        </div>
      );
    }
  }

  private renderTable() {
    if (!this.beers.length) {
      return;
    }

    return (
      <table className={styles.beerList}>
        <thead>
          <tr>
            <th />
            <th>Name</th>
            <th>Tagline</th>
          </tr>
        </thead>
        <tbody>
          {this.beers.map(({ name, tagline, image_url }) => {
            return (
              <tr>
                <td>
                  <img height={50} src={image_url} />
                </td>
                <td>{name}</td>
                <td>{tagline}</td>
              </tr>
            );
          })}
        </tbody>
      </table>
    );
  }

  private async getBeers() {
    this.isLoadingBeer = true;

    const response = await fetch("https://api.punkapi.com/v2/beers");
    this.beers = await response.json();

    this.isLoadingBeer = false;
  }
}
```

And use it in the main app:

_./browser/app.tsx_

```tsx

export default class App extends hyperdom.RenderComponent {
  private hideGreeting = false;
  private userName = "";
  private beerList = new BeerList();

  renderHeader() {
    return (
      <div>
        <h1 className={styles.hello}>Hello from Hyperdom!</h1>
        <a href="#" onclick={() => (this.hideGreeting = true)}>
          Next
        </a>
      </div>
    );
  }

  renderBody() {
    return (
      <div>
        <label>
          What is your name? <input type="text" binding={[this, "userName"]} />
        </label>
        {this.userName && (
          <div>
            You're now a <strong>hyperdomsta</strong> {this.userName}
          </div>
        )}
        {this.userName && this.beerList}
      </div>
    );
  }

  render() {
    return (
      <main>{this.hideGreeting ? this.renderBody() : this.renderHeader()}</main>
    );
  }
}
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKA5lA9gIwIZQHQAmeALgsiAMboB2xMtSIBMFU2ATjAAQC26BAV1hcAOiABUeCnDhiR1EAF8ANCAjVmADzwALYjyhJQVWvWKMAPHoMA-efKsxsBO9RHELxCMVg2AChwUMFBcAMrYGpjomhYA9F4-MK7uFjwwxNhcFDoccOkAvGIAqgAqAGIAtAAcYlyxrnE6Ti721BZRBACeyR4EEABuXBAEhSDYAA7jYjZxff3Jbh5wFOwQ48RccOwUo1sUsZjs6ADueeyx6loksiAzscur6w0H_N2tjfpQrkqq49gUAGtsCgYHgAFZwGhGSg0OgMRAgYDyLiiEDUbBpMSIVEg4gVOAZdh0AgVKg8cboPIVUhiZTI1H9GDsOAQGhY1EARjwAAYebT6WJmA81l42UhUfzqCixDxsOp2WJLjBtNYoJLpSBhesbtikVKUaiCRxiAqQH9tsEhhplbpPlwKhV0ON6OqDWJMAJoARTeagiEPV6rVdVXJ9SoBUwYM7rdQKBB4Oy9QbUTpOs72AR0DxTbyAExc7mujXENPwFYi00AZjwAFY8BzQyjw_rBTB-gARKP0Zix-M6rhJt1mwLBCoejSwdimth0AmNrjNjUAmCdY7oDP9gDaAF15IofprtgcjqcmbEJuNrppoSY4eYERByeuNuIuNg4FxU-nMzwuGAjr-YhfkyP5iAA3PIj4UkSXCvu-mwlrAH7_lmqJ4PciHwFIMjgZBT4wQAQjATIADIQASf4AWhsREaR5EmiAEFuNQyrQRszBgNgQgbKw74fgAgpMXDKnCBAfsBGZZngABK3ZMgAwlmFIsbQA70uMqz9NgdCfsMMAAOKcOk6goFw-R_rgeRMSiGkDNp3ACGcAByGLcOZciMepmn2VwmDEewZEUeZLHHFwtEBfRAAUACUTH0pw1rsAAEs0TIxWp-oopwxACOwUqRfSyYWHMrjJkVOgclkbAyC5aT5MABKdEhujBBgig2ClUAYJRqFJaWkk8AAhI0HKlWVKIWJkOicGAowAMS1DQrAQIC9XpfkNhcJFxA6ORuh6YZxFeNQpnmcQ7ACDA0XtYV41cE5Im3UV55jc9JW3bF9KKK0WVyewBGvOlg6_TleVbU9XDFQMr1lRYbB-V8EPJgA6jkGzkVwnToLlXDomkAD8kPqOMAgbCWzqjHQmgMb5lwmfVm47eRyioo5TK1TAYjboodQw898PBHzBrAEzcB4Gz7Ac1wABk0vg5ld1Q_MSNlQAmtjADknC4ycb6QwSRwnTYEk_kacQGzQKCbSLu1ixLHPfQr42zNDKvXSrNt7fbrky3Lot4H5dEEo7zuxO9CufWGP1cAlzDsEDt3Zbl-UQ6kcrUDYnti7tzCHcZJ1cIT_ux0yANdOl2LF39KXOGl11xLK6gw5HTZ7vIB57MeJxnDR_mBcQV43rCZiMFBz6wW-4n9T-PWASAJtZrh1BjzBcEfo1SGz9RG9YdINxxcvpjsJxQRhf5GUonjMDYgbJnWVwGRoOo18IasJ334-wIwAA-rlUA3-dO-bdmKsXHhxLiUAeLVQ_OFfuwlqbdint-KSslEqKSfCpDYg5bJaR0uREi6BnAmXCmZCyUArJeTsjpQOzJsT8XYOwbAnQLDhU2uZHcB9fqJQTgrCAYAtr-3wYQvoJ1wrRQvmVJOYMlY2AIUQk6eBFEu3mPfJswlyHcGBgaKRKcnYGhkSrCaHpiDEBoFwJaUAVoAjWuIjaD9bZ4FxOFOAMUeZ9DgNgTAsARhZzwEI-RKBwo3T0eNJK2BGR6xoYYyGBxSamIztE3xJd2AlE8bAVxKtlFCxbgaEOC5o44J8sk1JXiYA8OTHwrag1_Y0LFrAE6O1xFaJBsnVR-TmLJh0fLZ2GRSlVT4hzeqO8xY0P7sEu6kMdrNCFkVc6MzYY7V5tEiaO0bAcziKs5ZkydA2FSU_FiGydnRI2eweZhzpmZOIB0N4IThY1P8mLWU4xIqRWALjVyLNH6WJYizT-IJf7sBCIoWx1stldIKrcnppytmzJaJCiZRMeCmSaBAFAeh6o1m5DzPY9U_k_z_jzeoML9HxDhQixWxAXDACvooDZZLyULKpV85-tLSXzNDnMrZOSJnAryRy65QsNlpKSB9e-jtKG4O4O-TosYuBOIeeUg0gi4ByJEYE8-Z0LowE4QaEwFFOBwGUnkUh2Bjhyg2GAdI2QCrzxMeMOAiBYjnnGBAPAJNqBAhdVILMsR-i5gOA8sQ3L7F7VqSas13gY7wCNaCCENAYo6pRMq1VxCNVkIoVHagjsO5HkON3M8SptCkCHqYeEah8Ivknp-aeqEUJzwXtmTyy8K1cEEuMLeYh0IXiXvIBteALzdkipmCgAg0i0ADq8FmIVW2TBipHHN-w82nnOMM7CZBjDDzLYgNAWBcCRWuU0-kYBYQVE4jwaAnRsRiE6oyLwFBMgPUurSVtqxcAsw8dQOA-ImR8KYuK6gLUuroAkVTPE50IhwGPewHg2IBCTCZPejN_6A593ohIqIGYmSknQF1CYeRsRUFw_a7VwD5AoaDmTdg6H1xxzHOgExWZsQcnGJoTYOHhhcEsWi4gKBOCdD_a0cjEUKKUrpAB0ZaHFnYOcGqpj3IWMCYUCoEApATCQBQOCSEChyC3hHgiQcYgyQusnAAeXWKyT9iZbpiEhLlIIABZCY7JzqXTE8mMQljMDsk3GIeAAA2Z9gpF4gG3G5ocEJNCmk4P8BiYWNQRbKDF9cnRTR9oi0WQ0gCKAMUrlquLqIjj0fbBAKc4obPbHnI7bNigatAA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

<!-- tabs:end -->

?> Since `this.beerList` is a component, we can specify it in place in the jsx. Hyperdom will implicitly call its `render()` method.

## Routes

Routing is essential in most non-trivial applications. That's why hyperdom has routing built in - so you don't have to spend time choosing and implementing one.

We are going to add new routes to the beer site: `/beers` - to show the beers table - and `/beer/:id` - to show an individual beer. And, of course, there is still a `/` route.

First we need to tell hyperdom that this the routing is involved. We do this by mounting the app with a router:

<!-- tabs:start -->

#### ** Javascript **

_./browser/index.js_

```js
const hyperdom = require("hyperdom");
const router = require("hyperdom/router");
const App = require("./app");

hyperdom.append(document.body, new App(), { router });
```

#### ** Typescript **

_./browser/index.ts_

```ts
import * as hyperdom from "hyperdom";
import * as router from "hyperdom/router";
import App from "./app";

hyperdom.append(document.body, new App(), { router });
```

<!-- tabs:end -->

Next, on the home page, we specify what there is to render on the root path - `/` - and also add a link to `/beers`:

<!-- tabs:start -->

#### ** Javascript **

_./browser/app.jsx_

```jsx
const routes = require("./routes");

module.exports = class App {
  constructor () {
    this.beerList = new BeerList()
  }

  routes() {
    return [
      routes.home({
        render: () => {
          return this.hideGreeting ? this.renderBody() : this.renderHeader()
        }
      }),
      this.beerList
    ]
  }

  renderLayout(content) {
    return <main>{content}</main>
  }

  renderBody() {
    return (
      <div>
        <label>
          What is your name? <input type="text" binding="this.userName"></input>
        </label>
        {
          this.userName && <div>You're now a <strong>hyperdomsta</strong> {this.userName}</div>
        }
        {this.userName && <a href={routes.beers.href()}>Have a beer</a>}
      </div>
    )
  }

  renderHeader() {
    return (
      <div>
        <h1 class={styles.hello}>Hello from Hyperdom!</h1>
        <a href="#" onclick={() => (this.hideGreeting = true)}>
          Next
        </a>
      </div>
    );
  }
}
```

#### ** Typescript **

_./browser/app.tsx_

```tsx
import routes from "./routes";

export default class App extends hyperdom.RoutesComponent {
  private hideGreeting = false;
  private userName = "";
  private beerList = new BeerList();

  routes() {
    return [
      routes.home({
        render: () => {
          return this.hideGreeting ? this.renderBody() : this.renderHeader();
        }
      }),
      this.beerList
    ];
  }

  renderLayout(content: hyperdom.VdomFragment) {
    return <main>{content}</main>;
  }

  renderHeader() {
    return (
      <div>
        <h1 className={styles.hello}>Hello from Hyperdom!</h1>
        <a href="#" onclick={() => (this.hideGreeting = true)}>
          Next
        </a>
      </div>
    );
  }

  renderBody() {
    return (
      <div>
        <label>
          What is your name? <input type="text" binding={[this, "userName"]} />
        </label>
        {this.userName && (
          <div>
            You're now a <strong>hyperdomsta</strong> {this.userName}
          </div>
        )}
        {this.userName && <a href={routes.beers.href()}>Have a beer</a>}
      </div>
    );
  }
}
```

<!-- tabs:end -->

The original `render()` method is gone. Two other special methods - `routes()` and (optional) `renderLayout()` - took its place. The former one is where the magic happens, so let's take a closer look. In a nutshell, `routes()` returns a "url -> render function" mapping. A particular render is invoked only if the current url matches. The "key" in that mapping is not actually a string url but a route definition. `routes.home()` in the above example is a route definition.

We declare those route definitions separately so that they can be used anywhere in the project:

<!-- tabs:start -->

#### ** Javascript **

_./browser/routes.js_

```js
const router = require("hyperdom/router");

module.exports = {
  home: router.route("/"),
  beers: router.route("/beers"),
  beer: router.route("/beers/:id")
};
```

#### ** Typescript **

_./browser/routes.ts_

```ts
import * as router from "hyperdom/router";

export default {
  home: router.route("/"),
  beers: router.route("/beers"),
  beer: router.route("/beers/:id")
};
```

<!-- tabs:end -->

A route definition can be specified in the array returned from the `routes()` method. It can also generate a path for html links - e.g. `routes.beer.href({id: 23})` returns `/beers/23`.

There is one other thing that can be a part of the array returned by `routes()`. If you look closely at the above example, you'll notice `this.beerList` is also there. This works because `this.beerList` itself a has a `routes()` method:

<!-- tabs:start -->

#### ** Javascript **

_./browser/BeerList.jsx_

```jsx
const routes = require("./routes");

module.exports = class BeerList {

  get beerId() {
    return Number(this.beerIdParam)
  }

  async onload() {
    this.isLoadingBeer = true

    const response = await fetch("https://api.punkapi.com/v2/beers")
    this.beers = await response.json()

    this.isLoadingBeer = false
  }

  routes() {
    return [
      routes.beers({
        render: () => {
          return <div>{this.isLoadingBeer ? "Loading..." : this.renderTable()}</div>
        }
      }),
      routes.beer({
        bindings: {
          id: [this, "beerIdParam"]
        },
        render: () => {
          return <div>{this.isLoadingBeer ? "Loading..." : this.renderCurrentBeer()}</div>
        }
      })
    ]
  }

  renderCurrentBeer() {
    const beer = this.beers.find(beer => beer.id === this.beerId)
    return <img src={beer.image_url}/>
  }

  renderTable() {
    return (
      <div>
        <table class={styles.beerList}>
          <thead>
            <tr>
              <th />
              <th>Name</th>
              <th>Tagline</th>
              <th />
            </tr>
          </thead>
          <tbody>
            {this.beers.map(({id, name, tagline, image_url}) => {
              return (
                <tr>
                  <td>
                    <img height="50" src={image_url} />
                  </td>
                  <td>{name}</td>
                  <td>{tagline}</td>
                  <td><a href={routes.beer.href({id})}>show</a></td>
                </tr>
              )
            })}
          </tbody>
        </table>
      </div>
    )
  }
}
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKAdAIwIZplATgYyVHwHsA7AFxkqRGAB0yACJ-kAB13hgrjcSYBtRixZtqANzYAaEaLYALAJ7sYuACYkAtmzkBdWc1YcoAVwDmEMnyRC5YkBVwZrYEri0BaXKcoQtMLpGeowAvowgodIgVuowAB4oChRaUEQgpJTUFLQAPACEACIA8gDCACoAmgAKAKJMyakAfIy5jVAtRm0wGOqdoky5FBAUsE3VGAQ4TADKLupoJPG5APTDozD9orkBFBhM-AqTcDwAvGwAquUAYp4AHGxMK1urCj19jHK5i-pKWyy5dQQCRMCDqc4gDDsdhsJqrIESTr2QZwfC4CDsChMOAECE4_ArNC4EgAdxOuBWsQSKAAVjY4StUejMS9CSRfp1XikOhEohwMPgANYYcwwWlwcjpTJUGiIOhyNhkDABfjGZSqDTaTyiiieOB7XBUdTeEimYZkcwyBUgCRqOAQciqtgARhQAAZ3VajGw4kyMcNHbY2AAJFRqTRaJiFGBaEhMABSMy9Di0GCsTpiZDiiXayeMfsxNgEDCMDn1kwoGfYk3w0ypOe5TE8nhIqjIeYcaFM0HUVZr0y7PdBWepuZAcii1ribbiZHwEHgqpLAzYmGwUE87DMljInicLjgbg83l8wxVQZAUAwVH1HeMa5wm64J116vD2gzV5vlZAhhXIDfTUdAvL94B_Cc_2MOIJGjGdqHnRdbGXeR-SmDcuyzWBcE_a8wKCFhJ29EBBRgJQSXcdQiyEEIyHCMhImifFCWJMk1BWKF2HFeIpXIGUcjlTJ9QaMMgKYU4mC4ABHbsuAACkUESIzYABKABuRhBKxfUlFgOAxIkmBpIgOS2BQRkKB0-AUHwOAbDUjTyCEgAhGA1AAGQgITxKkmSYHkkAzJc9zPJ_ZSHOsLFiTNeB9J84y_NMlYopvFT1PbMhY3UUxYBQBJ2HcXh9PwK9bKYABBaEmGQzSfHwCh3CYWTlKq5EKAUTz0Fc3APK8pgyBgEkmCC7qQqaidPiMZL4CalrSwMihTFwZhhDmlgprgJJtD85CBjW6g4lwAQZtOJpZt23auAWpamDajr2riABxLgeCscwmAAfhu9qNq4EdcCc9klBmgRbp-_a1GDd41DG1bRDo87QmUyCBlBzrgtvOaaIIia9r-tyMCUU0KFk6Vsmanb5sW5gdjTMgmmAUnKFCVZUysLY6LkX6DoB34Zopy6qca5EAQRf5dtyK91zF86AHUjixTymEJxa-uVGBPtyKx2DNG6wwhKh4h_Jg0FiV79e-lBTHJAA5NXYVWLWzWl7YVklnBnZYCnztRq21FtgImAAMkDwZRcqU0AHIuD60kmH2XJ9WJC0mkAiNy1WRPyHMU7gB9m21eZlZReFuGS89vO_bVoOQ9yfYFC4MBTmAda0dwDb65gMAmtCJpgwwW04-NrrVgwJp4fFovgTFsKjA5ybwdwSHemh8nkQF675NhwEp7LwYFGdA4SrgJvtN0pIcCgEge8hqBL6YMBiUjUMNQjfJXmdD3BjrhuIQAYkecgxUIBCibsdU6slUb3RgE9Vy5o3riScKYGAyke67xYNbBIlZYYAnYs7eEO85r2VnmEXkjECDMVJOSFYw0eoUC4jxLIsoMiOSxKnbQsVDK-X8mw4CRDNLYgsrpDhRkTIBXMpZDaNk7JpX4etYRXDErrVShNTK2UxR5QKnpcSxUMClRoSFWacgdRDzUAASXUHzNePBBbW1MFobAuAIEW2wGY9QExnBaBntjdKLBdFKDnEwcgl9eiWLmqjTybkSC9FesNfSiDAg-NELI-A-VrAwH0hgEkaYsRgB4IcbhFAKDsDgIgFY7F2AQBQNrMgwoKnWW0CsCQAAmQkXU7KtWcW0jJWSRgGTgKkk44pyAww6R1CJUSgQWlieJMAGAoAnHGok9aoSBjr2WiXFuLi26yS9qILmagjrNROmdc6ezrHXW3oiXOFtxnRKmV1D6xhIl3PMCgN5jwQYW32bgcoWBYDd3wYiXe48BiI2RnsomVktk7N3ibLMr0SknNOaCdQAhBCg2kPeLq5j3HKjYFjU5hFkXfMOWJHOaDKYXNFtcsZcBnmTPMLEz6bB6WvTeSgD5X0OrfNKItX6FBhoAsnkC7BTAQVwy8aIAlc9cYHV5bgflgrV5zX4VsuJnS7QoEgFmWSarjlbJQGCMSpwEEatwOYyVe0rrU38G9fETcDX-BFDAAA-otKAoRniLM5gvX5aB_nKtWec5gm9zqXM_kMP56SdG2RPoIqFXVaGoNFQCNq7xP4DCGLgDN4s2pPBzZmtqTR_YwFWEWilhaFBNF-eYKAVhS1rCrRW7YeavUppdk4HNZa3i9C7RQH4fxm00o2lsjaqZ2CyR2WCTFSoAiYr2LW-tmKnWijdbgD1RzyXtqDdaoW27c3ZubWGigHx93Is1loN6bwIDmGSBCAArG6R49rgArtde60I-aj0TxPQW05Qw-jAFnTAQuv7v2FsAwuut_VQOnuRfBwYv7a4NB_s3SFI6upJAblO9QiMe5wAUKSEeDIwNno7Yesjlr4N4YpWWgdEa1hRrwcK6eiy6IMRAExIklC2L1nFAwvitB-E8PkfFbhikPwgD4SwiSkLcCidETwpKcnlFzhkxVdgCmEpiI4qpxgPCUAcX2rJTQ-A7HZHQIDGdA1yrQiapi4AsnorycRmlDjXGWJUJbnSAT2QhMyamvJ7ynCxMKRfg0wLemMrsjUbleI-VDRaJOYRgIAhAsoCmv5FYKlIKjrS3JjLkKsujpy3ILZ-XnOFeisVtpKxEBghUmENzfIPM8YpKfKyUjfNMMQLWkgmAoC6sBoG--vFPCzK0NAJQAgQw4FtMMfA-wMFIJkOVdEczMVwAPHqNQEAwBpTnufW-cZkIG11PuVw7gtACFMNCNQi2TgHYmq3WhJzFgaDUJ4Ugt8oQnAEN9q8xSYBPfSi9gxTg3sUU-4sQp2gBDOnYPEbEJA63qCYHW29FBzBcCUCDxgYOhInsMATrEebkLVnUAy-HbpEcg8iKEUIQA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

#### ** Typescript **

_./browser/BeerList.tsx_

```tsx
import routes from "./routes";

interface Beer {
  id: number;
  name: string;
  tagline: string;
  image_url: string;
}

export default class BeerList extends hyperdom.RoutesComponent {
  private isLoadingBeer = false;
  private beers: Array<Beer> = [];
  private beerIdParam: string = "";

  private get beerId() {
    return Number(this.beerIdParam);
  }

  async onload() {
    this.isLoadingBeer = true;

    const response = await fetch("https://api.punkapi.com/v2/beers");
    this.beers = await response.json();

    this.isLoadingBeer = false;
  }

  routes() {
    return [
      routes.beers({
        render: () => {
          return (
            <div>{this.isLoadingBeer ? "Loading..." : this.renderTable()}</div>
          );
        }
      }),
      routes.beer({
        bindings: {
          id: [this, "beerIdParam"]
        },
        render: () => {
          return (
            <div>
              {this.isLoadingBeer ? "Loading..." : this.renderCurrentBeer()}
            </div>
          );
        }
      })
    ];
  }

  render() {
    if (this.isLoadingBeer) {
      return <div>Loading...</div>;
    } else {
      return (
        <div>
          <button onclick={() => this.getBeers()} disabled={this.isLoadingBeer}>
            Have a beer
          </button>
          {this.renderTable()}
        </div>
      );
    }
  }

  renderCurrentBeer() {
    const beer = this.beers.find(beer => beer.id === this.beerId);
    return <img src={beer.image_url} />;
  }

  private renderTable() {
    if (!this.beers.length) {
      return;
    }

    return (
      <table className={styles.beerList}>
        <thead>
          <tr>
            <th />
            <th>Name</th>
            <th>Tagline</th>
            <th />
          </tr>
        </thead>
        <tbody>
          {this.beers.map(({ id, name, tagline, image_url }) => {
            return (
              <tr>
                <td>
                  <img height={50} src={image_url} />
                </td>
                <td>{name}</td>
                <td>{tagline}</td>
                <td>
                  <a href={routes.beer.href({ id })}>show</a>
                </td>
              </tr>
            );
          })}
        </tbody>
      </table>
    );
  }
}
```

<iframe src="https://codesandbox.io/api/v1/sandboxes/define?embed=1&parameters=N4IgZglgNgpgziAXKA5lA9gIwIZQHQAmeALgsiAMboB2xMtSIBMFU2ATjAAQC26BAV1hcAOiABUeCnDhiR1EAF8ANCAjVmADzwALYjyhJQVWvWKMAPHoMA-efKsxsBO9RHELxCMVg2AChwUMFBcAMrYGpjomhYA9F4-MK7uFjwwxNhcFDoccOkAvGIAqgAqAGIAtAAcYlyxrnE6Ti721BZRBACeyR4EEABuXBAEhSDYAA7jYjZxff3Jbh5wFOwQ48RccOwUo1sUsZjs6ADueeyx6loksiAzscur6w0H_N2tjfpQrkqq49gUAGtsCgYHgAFZwGhGSg0OgMRAgYDyLiiEDUbBpMSIVEg4gVOAZdh0AgVI4CLzUFAVUhiZTI1H9GDsOAQGhY1EARjwAAYebT6WJmA81l42UhUfzqCixDxsOp2WJLjBtNYoJLpSBhesbtikVKUaiCRxiAqQH9tsEhhplbpPlwKhV0ON6OqDWJMAJoARTeagiEPV6rVdVXJ9SoBUwYM7rdQKBB4Oy9QbUTpOs72AR0DxTbyAExc7mujXENPwFYi00AZjwAFY8BzQyjw_rBTB-gARKP0Zix-M6rhJt1mwLBCoejSwdimth0AmNrjNjUAmCdY7oDP9gDaAF15IofprtgcjqcmbEJuNrppoSY4eYERAeON1xtxFxsHAuKn05meFwwEcf5iN-TK_mIADc8iPs-RJcG-H6bCWsCfgBWaong9xIfAUgyBBUFPi-XAAEIwEyAAyEAEv-gHobEJHkZRJogJB1DQYRZKztRaFiBhHEJsxrTKjBGzMGA2BCBsrAfp-ACCkxcMqcIEJ-IEZlmeAAEroOS8AAMJZs-1BmAO9LjKs_TYHQX7DDAADinDpOoKBcPk_64HkLEomZAyWdwAhnAAchi3CuXIAn6t5FlWZgpHsBRVGuUZxzEbF8XEAAFAAlCx9J8XAWUmfqKKcMQAjsFKm70smeW6FmMDpYOybFd2TLYgV-Q2IVTVNSVZVSsQOiUboNn2aRFLOQA_FwA1DZw1rsERrwFdiM1wHgc3MOwAASzRMllnndQuVUGoomV0kVBqrXgMUMXOF3bgdiitM181kdgnTaRlt5mNiqm_ngABqv5lOwwJpLQmVdQavXlVwqRytQNjAN9tCKHEsrqDYj3PVwG1Mjtzh7ZDjW4-kfVcOlx0ohYcyuIdcM6ByWRsDIQVpPkwAEp0yG6MEGCKDYO1QBgXF_ltpZqTwACEjQcnTh0WJkOicGAowAMS1DQrAQICHPtZ16VXYNzCjY5lIudN7ACDAmUC1TTUBYp9vU-e8vJrMAxu1w2X0k9bj6njC1LcTx0w1KlMXdTtPO3DbAxV8McogA6jkGyUVwH1lVw6JpFNFjqOM5LTaWox0JoTFcJglxORzm6rcoqL-UybMwGI26KHUXvu7EcfBF3BrAFdTfsC3XAAGRjxTidw9HkeHQAmtpADknDZyc75wwSRyUjYf1ZkacRbzQKCdYPg1rcPLd-_TLuz_Ttsx2fQ2X8F4-T4rX4qxzNU3cyugq1lAWW1sCMg3r_OI2AbDXyah7eYx0fZhj3PIA8exjwnDOHRVKjErw3lhGYRgbFYLwRUhLX8osUykKzHhViBEiHvk_FzZC5CeKYW5thaQNwWKEI2HlZhIBeKfX4jlViph2BiSCClJkUNhjYmoAIHgMV2AHRzjAbEW8nIHQyGgdQqjEKrEpAdR8wIYAAH0ypQDUcQfRKAWJ-3kEJQiolxJQEkizT89E4qMQUuXbsJCfzqS0jpOA-kCJGVoFDSKvkhhwDIugZwTkPEWzElADyplzJRN_nAbEMl2Cg06BYDxnVXI7gOpE6KsUACSBAAigx4JY6xFswrCK8ukqyuJK6VIIAVEmYcuABXkYow259rqdJqRiBBTYcYfk6LGLgNAMDOG6cdK6lFYnxMpIk1yVjrbNINCYKinA4CGTyBbbAxw5QbDAOkbIlMQB6GIOMLJsRzzjAgHgQu1AgSvKkFmWI_RcwHFijcCZl1hmZNOec7wpMjk0DyOCSE1B9o4xRCsmJcS-gbNikk9yMBsb-2KoI_KIcLq9MqnPH-QKGox0Dm1SGHUob016RHG-BoaaeyfmtVZ6KElYqmmINZGKUB4GFbUFawzA4lGwJgWAgDYH92TCC7q0DkynXOt1Cle0SbJirhoJyWSGWHRkVwOu58G7ulGRwDEbcY6LkOjSimdLT7TyZdPKOntXUD1RQKnlUi-UgG9ZSYVeBRXTXFS1dgukypzWIB4wBHq5XT0VU1ZVJ1MrHQer7HGgclkXQgGACmXruWYqZMS9VZNYZsvmAGoVwq5UHSbApFJ3AtWk1KrDZlCs7433aOSYgNA5mxigDrAEetHWhqGriDxRKO59DgFK2AIwOV4C5eslAHi7Zz26sA0BmRf7TziB6YgfbEbTyXRK-d9UH6brhrELtCr61HUQfi0m81I25LMLG0tezYUbF_hbK6mS8CQA0OlP99Lf7LoIC5fIWywWdKTb0_OPBnJ7A5hBoxIIzHsCgB3eoeK0k-Ssue6Vl6DV5oplLADQK8CwEpANL91Vy3UAfXYklTGp5z08Be5m0kW4c0YdhX-aUN3008E0Zw8rWVWMk-7Aand40DRsC3OIimFM6BsJK7RRkVPqbU_J69LtpMxx080STngOhvAMwOKjTI1qynGOlBqQwCANxUQ3LRQ6jINww6Y8xC4x0trLW28OHrqZGas91TwLQIsK0fM5JoEAUB6A5jWbkHdUPAB81hnD-mWWRfiNFvLMDiAuGACotGBWZMKxK0jDzOiKs1dC1JwrRWYFKy_sADV7B_4wDAE54Y_mBZwB0CcCBVX8uNZi4Z9g43vYPqVVe0T8QLP9xUxer2IK_Z-xQUeQ46CzxKm0KQXBph4RqFoa-ehX5KF_lQkBO5N3qHcLgldvi7A-F7x4LEN7T2LtcDkuMPhGELzUPkJ9vAF5uzpUzBQeRZhrqvFczAZKAOsoN2ALjQR73TosR2_sPbp5zg1WO-QFG95zvCRewhN7H2bvfax6DoymhKdOIklDEbaRsRvfWoI25sQxBnXpJkrnWOec6T55kgXaqOmtUxzpbrfEJdAtiIgYYAu9y45UIefHJ4MECbWhwk7d5GCIDQFgXAoHXhfrALCCoYkeDQE6NiMQQtGReAoJkR21taT_dWLgBuc7qBwHxEyPNtjWi82FugKGZc8RWIiHAG37A6lcAEJMJkHvUnUFYyM26GxBxRAzEyCoVBhYTDyNiUvbBHm4qQf7XPniqJWKhoXzaY50BHqzNiDk4xNCbHQEOqDQ6kvEBQJwTo4f69Ca8SV86De0qhoic4QV3fuS98nweUgJhIBCohFCUneCzuDjEFQJ80AmQAHl1isiD4mY6YhIRlSCAAWQmOybZMBpcaiHZgdkZLupiDwAABsRYQ4YEIA6aX-qIEImgponA_wTEUBYgMBZQCB64nQpo4OMBoBD-ViOsTEK0Vsn-9-IAhIuIpoAAoqEDWDgSAEcB3u2BAFOOKA_tsPOFtsgooFwUAA" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

<!-- tabs:end -->

When beer table page is visited for the _first_ time, an `onload()` method is called by hyperdom (if provided). In our example, it performs an ajax request to fetch the data. This way, even if the page is then reload whilst on `/beers` or `/beers/23` the data is always going to be there to render.

Speaking of `/beers/23`, note how the `:id` parameter is bound onto a component property using `bindings` property. This is very similar to the input bindings we saw earlier.

?> Note how we use a custom `beerId` getter to coerce `:id` param into a number. That's because all url bindings produce string values.

Learn more about routing [here](api#routing)

## Testing

We've touched all hyperdom bases - there aren't that many! - and this is definitely enough to get you started. To help you keep going past that, `create-hyperdom-app` contains a fast, _full stack_ browser tests powered by [electron-mocha](https://github.com/jprichardson/electron-mocha) runner and [browser-monkey](https://github.com/featurist/browser-monkey) for dom assertions/manipulations. It's only a `yarn test` away.
