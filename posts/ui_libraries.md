---
title: UI Libraries
publish_date: 2022-10-23
---

Basically, there are 3 types of UI libraries in frontend ecosystem:

-   CSS with superpowers
-   Functional libraries
-   Design system libraries

Let's talk about each of these types and decide whether or not we should use them.

# CSS with superpowers or CSS++

This category includes things like SASS, Less, Tailwind and many others.

Yep, Tailwind is not a 'second Bootstrap' because it doesn't have any ready components like buttons, tables and other stuff. Moreover, it lets you write regular CSS but with the help of utility classes and some constraints to make your design system more consistent.

```html
<!-- tailwind -->
<p class="text-lg font-semibold text-blue-800 p-4">Hello World!</p>

<!-- bootstrap -->
<button class="button">Click!</button>
```

SASS and Less are CSS preprocessors that add things like mixins, variables, nesting etc. Many of them are gonna be available in regular CSS, so these tools live the last days.

```css
@mixin button-base() {
	@include typography(button);
	@include ripple-surface;
	@include ripple-radius-bounded;

	display: inline-flex;
	position: relative;
	height: $button-height;
	border: none;
	vertical-align: middle;

	&:hover {
		cursor: pointer;
	}

	&:disabled {
		color: $mdc-button-disabled-ink-color;
		cursor: default;
		pointer-events: none;
	}
}
```

### Pros:

-   maybe mixing and nesting
-   easily customizable
-   ship faster sometimes

### Cons:

-   hate your job when you have to debug deeply nested sass classes

# Functional or behavior libraries

Radix, Headless UI, React Aria etc.

These are not about look of components at all. Accessibility and ease of customization are the main focuses here. Dropdowns, dialogs, tabs, sliders and others. You take working and accessible component and style it to your needs.

For example, Headless UI is designed to integrate beautifully with Tailwind:

```js
import { useState } from "react";
import { Dialog } from "@headlessui/react";

function MyDialog() {
	let [isOpen, setIsOpen] = useState(true);

	return (
		<Dialog
			open={isOpen}
			onClose={() => setIsOpen(false)}
			className="relative z-50"
		>
			<div className="fixed inset-0 flex items-center justify-center p-4">
				<Dialog.Panel className="w-full max-w-sm rounded bg-white">
					<Dialog.Title>Complete your order</Dialog.Title>

					{/* ... */}
				</Dialog.Panel>
			</div>
		</Dialog>
	);
}
```

### Pros:

-   fully accessible
-   easily customizable
-   ship faster
-   not reinventing the wheel

# Design system libraries

Bootstrap is probably the most popular one. You take one class or component and here is your button:

```html
<button type="button" class="btn btn-primary">Primary</button>
```

Easy? Yes, at first. But then a designer wants you to change some stuff here and there. Easy? Not at all. By using ready design systems you have to accept and understand the restrictions. Not only you but your designer and customer too.

### Pros

-   ship fast at first

### Cons

-   you will run into restrictions
-   hard to customize
-   all websites look the same

# Libraries in between

You've probably noticed that I haven't mentioned MUI, Chakra UI and some other libraries. Libraries that are somewhere in between. Neither fish or fowl.

In my opinion, it's our job as frontend engineers to think about styles and functionality of our interfaces and combine these two parts properly to make user experience better.

Abstracting both of these parts away into something like MUI just means you have to learn way weirder shit when you have a problem that these libraries do not solve. You need to know these libraries and their limitations very well in order to work around them at all.

# Conclusion

With all that said I do recommend you to try out functional libraries and forget about MUI.

Heavily inspired by [Theo's talk about css libraries](https://youtu.be/CQuTF-bkOgc).
