## Project Summary

In this project, we will learn how to create a side drawer that appears when clicking on a menu button. Since this module only covers HTML & CSS, I will show you a way to create a drawer with only HTML & CSS. There are other ways of creating a drawer using JavaScript as well.

## Steps

After each step, use git to add and commit the changes you have made to the project!

### Step 1.

Fork this repository to create your own copy.

### Step 2.

Make `index.html` and `style.css` files. Use HTML:5 snippet and link the style sheet to the html. We will also want to link the `reset.css` file that is included in the repo. Make sure to link `reset.css` before `style.css` so that the reset styled are applied first.

In this step, let's also go ahead and change the title for our website. You can make it whatever you want.

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Drawer</title>
  </head>
  <body></body>
</html>
```

</details>

### Step 3.

Let's create a black header and a black drawer on the left side.

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Transition</title>
  </head>
  <body>
    <header></header>
    <main>
      <section id="drawer"></section>
    </main>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
header {
  height: 80px;
  background: black;
  position: fixed;
  width: 100%;

  display: flex;
  align-items: center;

  color: white;
}

main {
  height: 100vh;
  padding-top: 80px;
  width: 100vw;
}

#drawer {
  width: 400px;
  background: black;
  height: 100%;
  border-top: 1px solid white;
}
```

</details>

### Step 4.

The idea is that the drawer will start off screen, and then we will have a button we can click to show or hide the drawer. So in this step, let's hide the drawer by using the transform property and move the drawer off screen

`transform: translateX(-400px);`

by using `translateX` we can move the drawer horizontally, and giving it a value of -400px, we are sayin that we want it to move to the left by 400px. Since the drawer has a width of 400px, that will move it off the screen and we can't see it anymore.

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Transition</title>
  </head>
  <body>
    <header></header>
    <main>
      <section id="drawer"></section>
    </main>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
header {
  height: 80px;
  background: black;
  position: fixed;
  width: 100%;

  display: flex;
  align-items: center;

  color: white;
}

main {
  height: 100vh;
  padding-top: 80px;
  width: 100vw;
}

#drawer {
  width: 400px;
  background: black;
  height: 100%;
  border-top: 1px solid white;
  transform: translateX(-400px);
}
```

</details>

### Step 5.

Now that we have the drawer off the screen, we want to create a button, that when clicked, will make the drawer appear. I do not expect you to know how to do this right now, or be able to figure it out on your own.
<br />
Let's create an input element of type `checkbox` and place it before our header. You'll see why we are doing this in a bit. Give it and id of `drawer-button`.
<br />
`<input type="checkbox" id="drawer-button" />`
<br />
We will use this checkbox element to determine if the drawer should be open or closed. In css, we can target a checkbox element by if it is checked or not. So in our css, let's make it so that if the checkbox is checked, we show the drawer by using the `transform` property and setting it to `translateX(0)`;

```css
#drawer-button:checked ~ main > #drawer {
  transform: translateX(0);
}
```

let's take a second to look at this css selector and really think about what is going on. `#drawer-button:checked` is saying we want to taget an element when the element with id `drawer-button` is checked. The `~` signifies that we want to target a sibling element of the `drawer-button` element. The sibling we are targeting is `main`. The `>` symbol says we want to target a child element. In this case we want to target the element with id `drawer`. And then we specify the styled we want to apply. So when the `drawe-button` checkbox is checked, we want the `drawer` element to transform and traslate on the x axis to the 0 position, or it's normal position in the DOM.
<br/>
Once you have this code in, you should see a checkbox in the upper left hand corner and when you click it, the checkbox will be checked, and the drawer will appear! Pretty cool, right?!

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Transition</title>
  </head>
  <body>
    <input type="checkbox" id="drawer-button" />
    <header></header>
    <main>
      <section id="drawer"></section>
    </main>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
header {
  height: 80px;
  background: black;
  position: fixed;
  width: 100%;

  display: flex;
  align-items: center;

  color: white;
}

main {
  height: 100vh;
  padding-top: 80px;
  width: 100vw;
}

#drawer {
  width: 400px;
  background: black;
  height: 100%;
  border-top: 1px solid white;
  transform: translateX(-400px);
}

#drawer-button:checked ~ main > #drawer {
  transform: translateX(0);
}
```

</details>

### Step 6.

This is already really cool! But it looks a little funny and not really intuitive to have to check a checkbox to make the drawer open. Clicking a button would make more sense. This is where a label could come in handy. You'be already learned that when you click on a label for a form element, it selects that element that the label is for. So if we make a label for our checkbox, we should be able to click on the label and it will check the checkbox for us. Another really cool thing about this is that the label can live wherever we want it to!
<br/>
Let's create a label for the `drawer-button` checkbox and have it live inside the header.
<br/>

```html
<label for="drawer-button" name="drawer-button">click</label>
```

Now when we click on the label, you can see that we can open and close the drawe!

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Transition</title>
  </head>
  <body>
    <input type="checkbox" id="drawer-button" />
    <header>
      <label for="drawer-button" name="drawer-button">click</label>
    </header>
    <main>
      <section id="drawer"></section>
    </main>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
header {
  height: 80px;
  background: black;
  position: fixed;
  width: 100%;

  display: flex;
  align-items: center;

  color: white;
}

main {
  height: 100vh;
  padding-top: 80px;
  width: 100vw;
}

#drawer {
  width: 400px;
  background: black;
  height: 100%;
  border-top: 1px solid white;
  transform: translateX(-400px);
}

#drawer-button:checked ~ main > #drawer {
  transform: translateX(0);
}
```

</details>

### Step 7.

Now that we have a label that we can click to open and close the drawer, let's hide the checkbox so that we can't even see it.

<br />

```css
#drawer-button {
  display: none;
}
```

<br />

And instead of showing the word `click` in the label, let's display content based on if the checkbox is checked or not. If it is not checked (meaning the drawer is closed) we want it to say `OPEN`, and if it is checked (the drawer is open) we want it so say `CLOSED`. We can user the `::after` pseudo selector to help us with this. Let's also give it a border and some paddiing to make it look like a button the user would want to click.

```html
<label for="drawer-button" name="drawer-button"></label>
```

```css
[name="drawer-button"]::after {
  content: "OPEN";
  margin-left: 24px;
  border: 1px solid white;
  padding: 16px;
}

#drawer-button:checked ~ header > [name="drawer-button"]::after {
  content: "CLOSE";
}
```

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Transition</title>
  </head>
  <body>
    <input type="checkbox" id="drawer-button" />
    <header>
      <label for="drawer-button" name="drawer-button"></label>
    </header>
    <main>
      <section id="drawer"></section>
    </main>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
header {
  height: 80px;
  background: black;
  position: fixed;
  width: 100%;

  display: flex;
  align-items: center;

  color: white;
}

main {
  height: 100vh;
  padding-top: 80px;
  width: 100vw;
}

#drawer {
  width: 400px;
  background: black;
  height: 100%;
  border-top: 1px solid white;
  transform: translateX(-400px);
}

#drawer-button:checked ~ main > #drawer {
  transform: translateX(0);
}

#drawer-button {
  display: none;
}

[name="drawer-button"]::after {
  content: "OPEN";
  margin-left: 24px;
  border: 1px solid white;
  padding: 16px;
}

#drawer-button:checked ~ header > [name="drawer-button"]::after {
  content: "CLOSE";
}
```

</details>

### Step 8.

We now have a working drawer and a cool looking button that we can click to open and close the drawer. One thing that we will want to add to make the user experience even better is a transition so the opening and closing effect is animated and takes a little time. Let's add a transition to the `#drawer` id selector in our css file.

```css
transition: transform 0.3s ease-in;
```

Super cool! But when you refresh the page, you might notice a strange transition effect that is happening on page load. The drawer at first appears and then translates off the page. Not the best user experience. We can fix this by adding a `script` tag to the head of our html document. Add `<script src="index.js"></script>` right before the `title` element in the head of our document. I'm not going to go into what script tags are since this module doesn't go over any javacript, but just know that this will fix the issue.

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <!-- this is to prevent transitions on page load -->
    <script src="index.js"></script>
    <title>Transition</title>
  </head>
  <body>
    <input type="checkbox" id="drawer-button" />
    <header>
      <label for="drawer-button" name="drawer-button"></label>
    </header>
    <main>
      <section id="drawer"></section>
    </main>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
header {
  height: 80px;
  background: black;
  position: fixed;
  width: 100%;

  display: flex;
  align-items: center;

  color: white;
}

main {
  height: 100vh;
  padding-top: 80px;
  width: 100vw;
}

#drawer {
  width: 400px;
  background: black;
  height: 100%;
  border-top: 1px solid white;
  transform: translateX(-400px);
  transition: transform 0.3s ease-in;
}

#drawer-button:checked ~ main > #drawer {
  transform: translateX(0);
}

#drawer-button {
  display: none;
}

[name="drawer-button"]::after {
  content: "OPEN";
  margin-left: 24px;
  border: 1px solid white;
  padding: 16px;
}

#drawer-button:checked ~ header > [name="drawer-button"]::after {
  content: "CLOSE";
}
```

</details>

### Step 9.

One last thing. If we add more content inside out `main` element, we will notice that we have to scroll down in order to see the content. We need to give a `position: fixed;` to our `#drawer` element so that it will be taken out of the flow of the DOM and the element defined below it can move up in the DOM. Let's add some paragraphs below the drawer so we have some content on our website.

## Solution

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <!-- this is to prevent transitions on page load -->
    <script src="index.js"></script>
    <title>Transition</title>
  </head>
  <body>
    <input type="checkbox" id="drawer-button" />
    <header>
      <label for="drawer-button" name="drawer-button"></label>
    </header>
    <main>
      <section id="drawer"></section>
      <section>
        <p>
          Lorem ipsum dolor, sit amet consectetur adipisicing elit. Modi
          expedita quis illum vitae laudantium! Recusandae minima debitis,
          laudantium reiciendis repellat omnis, ab consequuntur sunt totam eos
          quibusdam, nisi dicta nihil? Lorem ipsum dolor, sit amet consectetur
          adipisicing elit. Modi expedita quis illum vitae laudantium!
          Recusandae minima debitis, laudantium reiciendis repellat omnis, ab
          consequuntur sunt totam eos quibusdam, nisi dicta nihil? Lorem ipsum
          dolor, sit amet consectetur adipisicing elit. Modi expedita quis illum
          vitae laudantium! Recusandae minima debitis, laudantium reiciendis
          repellat omnis, ab consequuntur sunt totam eos quibusdam, nisi dicta
          nihil?
        </p>

        <p>
          Lorem ipsum dolor, sit amet consectetur adipisicing elit. Modi
          expedita quis illum vitae laudantium! Recusandae minima debitis,
          laudantium reiciendis repellat omnis, ab consequuntur sunt totam eos
          quibusdam, nisi dicta nihil? Lorem ipsum dolor, sit amet consectetur
          adipisicing elit. Modi expedita quis illum vitae laudantium!
          Recusandae minima debitis, laudantium reiciendis repellat omnis, ab
          consequuntur sunt totam eos quibusdam, nisi dicta nihil? Lorem ipsum
          dolor, sit amet consectetur adipisicing elit. Modi expedita quis illum
          vitae laudantium! Recusandae minima debitis, laudantium reiciendis
          repellat omnis, ab consequuntur sunt totam eos quibusdam, nisi dicta
          nihil?
        </p>

        <p>
          Lorem ipsum dolor, sit amet consectetur adipisicing elit. Modi
          expedita quis illum vitae laudantium! Recusandae minima debitis,
          laudantium reiciendis repellat omnis, ab consequuntur sunt totam eos
          quibusdam, nisi dicta nihil? Lorem ipsum dolor, sit amet consectetur
          adipisicing elit. Modi expedita quis illum vitae laudantium!
          Recusandae minima debitis, laudantium reiciendis repellat omnis, ab
          consequuntur sunt totam eos quibusdam, nisi dicta nihil? Lorem ipsum
          dolor, sit amet consectetur adipisicing elit. Modi expedita quis illum
          vitae laudantium! Recusandae minima debitis, laudantium reiciendis
          repellat omnis, ab consequuntur sunt totam eos quibusdam, nisi dicta
          nihil?
        </p>

        <p>
          Lorem ipsum dolor, sit amet consectetur adipisicing elit. Modi
          expedita quis illum vitae laudantium! Recusandae minima debitis,
          laudantium reiciendis repellat omnis, ab consequuntur sunt totam eos
          quibusdam, nisi dicta nihil? Lorem ipsum dolor, sit amet consectetur
          adipisicing elit. Modi expedita quis illum vitae laudantium!
          Recusandae minima debitis, laudantium reiciendis repellat omnis, ab
          consequuntur sunt totam eos quibusdam, nisi dicta nihil? Lorem ipsum
          dolor, sit amet consectetur adipisicing elit. Modi expedita quis illum
          vitae laudantium! Recusandae minima debitis, laudantium reiciendis
          repellat omnis, ab consequuntur sunt totam eos quibusdam, nisi dicta
          nihil?
        </p>
      </section>
    </main>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
header {
  height: 80px;
  background: black;
  position: fixed;
  width: 100%;

  display: flex;
  align-items: center;

  color: white;
}

main {
  height: 100vh;
  padding-top: 80px;
  width: 100vw;
}

#drawer {
  width: 400px;
  background: black;
  height: 100%;
  border-top: 1px solid white;
  transform: translateX(-400px);
  transition: transform 0.3s ease-in;
  position: fixed;
}

#drawer-button:checked ~ main > #drawer {
  transform: translateX(0);
}

#drawer-button {
  display: none;
}

[name="drawer-button"]::after {
  content: "OPEN";
  margin-left: 24px;
  border: 1px solid white;
  padding: 16px;
}

#drawer-button:checked ~ header > [name="drawer-button"]::after {
  content: "CLOSE";
}

section {
  padding: 32px;
}

p {
  margin: 16px 0;
}
```

</details>

## Submit project

The final step, and one of the most important! Use git to add and commit any new changes, then push those changes to your reposiroty on github.

I hope this was a fun project for you to build! Drawers are very common, and very useful, especially on mobile devices where screen space is limited. If you plan on learning JavaScript and React in my other modules, you will learn how to create drawers in a more intuitive way! Make sure you submit this project in the `Guided project(s)` section for this unit. Just copy the url for your repository, paste it and click send!
