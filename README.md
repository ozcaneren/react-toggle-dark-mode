### `create hook directory & create useDarkSide.js`

![image](https://github.com/ozcaneren/react-toggle-dark-mode/assets/100240225/a0ad1053-7e3c-4f38-93b6-984202db799e)

```bash
mkdir hook & cd hook
touch useDarkSide.js
```
### Code

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
### Code

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
