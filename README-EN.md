# Frontend Development Quality Checklist

[한국어](./README.md) | English 

## Overview
In the fast-paced world of web development, it's easy to overlook critical details. This checklist, which I've personally been using in my workflow, helps ensure comprehensive quality review at project completion. <br/><br/>
Created from practical experience and technical studies, this checklist incorporates best practices and is continuously updated to reflect current development trends. :) <br/>

Feedback and suggestions for improvement are always welcome. Let's build better development processes together! 🙌<br/>

I'll also share it with you on the [notion page](https://private-crab-648.notion.site/Frontend-Development-Quality-Checklist-1b69b72044de808c8094e45549e58eb5?pvs=4). You can clone it and use it as you like :)

## Checklist
### 1. Performance
- [ ] Measure performance using Lighthouse
- [ ] Image optimization
    - [ ] Are you loading images larger than the size you'll actually display?
    - [ ] Is lazy loading or preloading appropriate for your use case?
    - [ ] Can you use WebP format? (with fallback images for browser compatibility)
- [ ] Animation optimization
    - [ ] Can you separate layers in advance using will-change or translate3d properties?
    - [ ] Are there any properties causing unnecessary reflow or repaint?
- [ ] Bundle size
    - [ ] Measure bundle size (using tools like webpack-bundle-analyzer)
    - [ ] Are there areas where code splitting would be beneficial?
    - [ ] Can tree shaking be applied through partial imports?
    - [ ] Can SVG files be optimized with SVGO to reduce bundle size?
- [ ] Optimization of computationally intensive variables/functions
    - [ ] Can you optimize using useMemo or useCallback?
- [ ] Rendering optimization
    - [ ] When passing objects or functions as props to child components, are there unnecessary renders?
    - [ ] Can you use React.memo to prevent unnecessary re-renders?
    - [ ] When using global state management libraries, are there unnecessary renders?
    - [ ] Can you apply lazy loading or code splitting to improve initial load performance?
    - [ ] Are components properly separated into small units to prevent unnecessary re-renders when state changes?
- [ ] Rendering strategy optimization
    - [ ] Can you optimize rendering by appropriately using SSR/SSG/CSR/ISR?
- [ ] Font optimization
    - [ ] Can you optimize font loading with the font-display property?
    - [ ] Are you using minimized font files?
    - [ ] Are you using optimized font file formats? (with fallback fonts for browser compatibility)

### 2. Usability
- [ ] Enhance input element usability
    - [ ] Are there places where inputmode should be applied? (e.g., mobile number keypad)
    - [ ] Can you restrict user input by applying patterns to input elements?
    - [ ] Are placeholders clearly indicating what users should enter?
- [ ] Can debounce or throttle improve usability?
    - [ ] Can debounce be applied? (search functionality (with useDeferredValue), preventing duplicate button clicks, window resizing, auto-save, drag and drop, etc.)
    - [ ] Can throttle be applied? (scroll or mouse event handling, etc.)
- [ ] Mobile browser support range (based on my criteria: iOS 13+ and Android 8.0 (Chrome 68+))
    - [ ] Are you using the gap property with flex? (provide polyfill using @supports)
    - [ ] Are there any browser APIs or CSS properties beyond the support range? (check with [can i use](https://caniuse.com/))
- [ ] User feedback
    - [ ] Are you providing loading states to users during API calls?
        - [ ] Can you use Suspense?
        - [ ] Can you set a minimum delay time to prevent loading UI from flickering?
    - [ ] Are you providing error states to users during API calls?
        - [ ] Are you distinguishing between 400 and 500 level errors to provide appropriate messages?
        - [ ] Can you use error boundaries?
    - [ ] Are you providing appropriate messages when users navigate to non-existent pages?

### 3. Web Accessibility
- [ ] Check web accessibility using [accessibility tools](https://catstanets.tistory.com/167)
- [ ] Keyboard accessibility
    - [ ] Can all functions be operated with a keyboard?
    - [ ] Is keyboard focus clearly visible?
- [ ] Have you applied aria-label to buttons that only contain icons or images?
- [ ] Are alt tags appropriately written?
- [ ] Do you provide "skip to content" links so users can navigate directly to content? [Reference](https://kittygiraudel.com/2020/12/06/a11y-advent-skip-to-content/#skip_link-note)
- [ ] Have you implemented components with accessibility in mind using aria-expanded, role, etc.? [Reference](https://github.com/scottaohara/accessible_components)
- [ ] Are you using aria-disabled instead of disabled to ensure buttons aren't omitted from the accessibility tree?
- [ ] Can modals be closed with the ESC key?
- [ ] Have you avoided using properties that remove elements from the accessibility tree, like display: block?
- [ ] Have you used .sr-only class to provide information for screen reader users? [Reference](https://kittygiraudel.com/2020/12/03/a11y-advent-hiding-content/)

### 4. Code Improvement
- [ ] Are there functions doing too many things?
- [ ] Are there components doing too many things?
- [ ] Are any components too large?
- [ ] Are there parts that could be separated into hooks?
- [ ] Is there any duplicate code?
- [ ] Are function and variable names clear?