### `React Light Dark Mode`

Hello today we are going to apply the light dark mode transition in React with you. (with [Tailwind](https://tailwindcss.com/))

![](https://github.com/ozcaneren/react-toggle-dark-mode/blob/master/public/GIF.gif)



### `Setup Tailwind`

[Tailwind install with Create React App](https://tailwindcss.com/docs/guides/create-react-app)

### Installation

```bash
npm install -D tailwindcss
npx tailwindcss init
```

### tailwind.config.js

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
  darkMode: "class",
}
```

### index.css

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### `create hook directory & create useDarkSide.js`

![image](https://github.com/ozcaneren/react-toggle-dark-mode/assets/100240225/a0ad1053-7e3c-4f38-93b6-984202db799e)

```bash
mkdir hook & cd hook
touch useDarkSide.js
```
### useDarkSide.js

```js
import { useEffect, useState } from "react";
export default function useDarkSide() {
  const [theme, setTheme] = useState(localStorage.theme);
  const colorTheme = theme === "dark" ? "light" : "dark";

  useEffect(() => {
    const root = window.document.documentElement;
    root.classList.remove(colorTheme);
    root.classList.add(theme);
    localStorage.setItem("theme", theme);
  }, [theme, colorTheme]);

  return [colorTheme, setTheme];
}
```

### `create components folder & create Switcher.js`

![image](https://github.com/ozcaneren/react-toggle-dark-mode/assets/100240225/89d9e8e2-9a5b-4ec4-b922-3e72f9c98938)

```bash
mkdir components & cd components <br/>
touch Switcher.js
```

### Install Module [react-toggle-dark-mode](https://www.npmjs.com/package/react-toggle-dark-mode)

```bash
npm install react-toggle-dark-mode
```
### Switcher.js

```js
import React, { useState } from 'react';
import useDarkSide from '../hook/useDarkSide';
import { DarkModeSwitch } from "react-toggle-dark-mode";

export default function Switcher() {
  const [colorTheme, setTheme] = useDarkSide();
  const [darkSide, setDarkSide] = useState( colorTheme === "light" ? true : false );

  const toggleDarkMode = (checked) => {
    setTheme(colorTheme)
    setDarkSide(checked);
  };

  return (
    <>
      <div>
        <DarkModeSwitch
          checked={darkSide}
          onChange={toggleDarkMode}
          size={33}
        />
      </div>
    </>
  );
}
```
### `App.js`

```js
import Switcher from "./components/Switcher";

function App() {
  return (
    <>
      <div className="container mx-auto my-10 flex flex-col justify-center items-center text-center gap-8 bg-white dark:bg-black">
        <Switcher />
        <h1 className="font-bold text-2xl text-black dark:text-white">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Nulla at volutpat diam ut venenatis tellus. Volutpat diam ut venenatis tellus. Justo laoreet sit amet cursus sit amet dictum. Facilisis leo vel fringilla est ullamcorper eget. Pulvinar neque laoreet suspendisse interdum consectetur libero id faucibus. Vel turpis nunc eget lorem dolor sed. Hendrerit gravida rutrum quisque non. Rhoncus urna neque viverra justo nec ultrices dui sapien. Velit egestas dui id ornare arcu. Placerat duis ultricies lacus sed turpis tincidunt id aliquet risus. Dictum non consectetur a erat nam at lectus urna.

          Eget sit amet tellus cras adipiscing enim eu turpis. Ac tincidunt vitae semper quis lectus nulla at. Nunc congue nisi vitae suscipit. Euismod elementum nisi quis eleifend. Diam maecenas sed enim ut sem viverra aliquet eget. Nisi porta lorem mollis aliquam ut porttitor leo a diam. Potenti nullam ac tortor vitae. Nunc congue nisi vitae suscipit tellus mauris. Nibh praesent tristique magna sit amet purus gravida. Amet consectetur adipiscing elit duis tristique sollicitudin nibh. Ornare quam viverra orci sagittis eu. Morbi tempus iaculis urna id.

          Pretium vulputate sapien nec sagittis aliquam malesuada. Phasellus egestas tellus rutrum tellus pellentesque. Cursus risus at ultrices mi tempus imperdiet nulla. Ut aliquam purus sit amet luctus. Massa eget egestas purus viverra accumsan in nisl nisi. Ut diam quam nulla porttitor massa id neque. Adipiscing tristique risus nec feugiat in fermentum. Et tortor consequat id porta nibh venenatis. Libero volutpat sed cras ornare. Urna nunc id cursus metus aliquam. Iaculis urna id volutpat lacus laoreet non curabitur gravida arcu. Id diam maecenas ultricies mi. Amet cursus sit amet dictum sit amet justo donec enim. Felis eget velit aliquet sagittis. Fermentum dui faucibus in ornare quam viverra orci. Accumsan tortor posuere ac ut consequat semper viverra nam. Ipsum suspendisse ultrices gravida dictum fusce ut placerat orci. Neque sodales ut etiam sit. Sed elementum tempus egestas sed sed risus pretium quam vulputate. Viverra nam libero justo laoreet sit amet.

          Leo vel orci porta non pulvinar. Iaculis nunc sed augue lacus viverra vitae congue eu. Turpis in eu mi bibendum. Arcu cursus euismod quis viverra nibh cras pulvinar mattis. Quis lectus nulla at volutpat. Faucibus turpis in eu mi bibendum neque egestas congue. Enim nunc faucibus a pellentesque. In iaculis nunc sed augue lacus. Potenti nullam ac tortor vitae purus faucibus ornare suspendisse sed. Ullamcorper velit sed ullamcorper morbi tincidunt ornare massa eget. Vel turpis nunc eget lorem dolor sed viverra ipsum nunc. Sit amet consectetur adipiscing elit ut. Nec sagittis aliquam malesuada bibendum arcu. Tellus rutrum tellus pellentesque eu tincidunt tortor. Blandit libero volutpat sed cras ornare arcu dui vivamus arcu. Sit amet est placerat in egestas erat. Bibendum neque egestas congue quisque egestas diam.

          Pulvinar etiam non quam lacus suspendisse faucibus interdum posuere lorem. Id donec ultrices tincidunt arcu non. Duis convallis convallis tellus id interdum. Sollicitudin nibh sit amet commodo. Mauris nunc congue nisi vitae suscipit tellus mauris. Maecenas pharetra convallis posuere morbi leo urna molestie. Ac tortor vitae purus faucibus ornare suspendisse sed nisi.
        </h1>
      </div>
    </>
  );
}

export default App;

```

