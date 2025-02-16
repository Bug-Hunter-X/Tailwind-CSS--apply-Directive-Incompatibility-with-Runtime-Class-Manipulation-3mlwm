# Tailwind CSS @apply Directive Issue with Dynamic Class Addition

This repository demonstrates an uncommon bug related to Tailwind CSS's `@apply` directive when used in conjunction with dynamic class additions in JavaScript frameworks like Vue.js.  The `@apply` directive, designed for compile-time style injection, doesn't work as expected when classes are added or modified at runtime via JavaScript.

## Problem Description

The core problem is that `@apply` is processed during the build step of your application, not during runtime.  Therefore, any attempt to use it within a custom Vue directive or similar mechanisms that dynamically update the DOM's class attributes will fail to apply the intended styles.

## Reproduction Steps

1. Clone this repository.
2. Run `npm install`.
3. Run the development server (instructions may vary depending on your framework). 
4. Observe that the div with the `v-myDirective` doesn't have the expected styles applied by the `@apply` directive. This is because the classes are added dynamically and not during the initial build phase.

## Solution

The solution is to avoid using `@apply` in contexts where classes are added or removed dynamically at runtime.  Instead, directly apply the individual utility classes within the dynamic class manipulation code.