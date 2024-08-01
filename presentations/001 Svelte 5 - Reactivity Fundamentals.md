---
marp: true
theme: default
---

# 001 Svelte 5 - Reactivity Fundamentals

Source: 
https://github.com/sveltejs/svelte/blob/9556bc48b7f0ac04dc121e73669e8eaa4a1a0aa3/documentation/docs/01-introduction/03-reactivity-fundamentals.md

---

## Introducing Runes

- Powerful primitives for controlling reactivity
- Function-like symbols
- Part of the Svelte language
- No imports needed

<!-- Speaker notes:
• Runes are Svelte 5's new way to handle reactivity
• Think of them as special instructions to the Svelte compiler
• Look like functions, but are part of Svelte's syntax
• No imports needed - available everywhere in Svelte code -->

---

## REPL (Read, Evaluate, Print, and Loop)
## [🔗 REPL Svelte 5](https://svelte-5-preview.vercel.app/)
[🔗 REPL Svelte 4](https://svelte.dev/repl)


<!-- Speaker notes:
• For the following examples we will use the Svelte REPL
• The Svelte REPL is an online interactive environment where you can write, 
  test, and share Svelte components. -->
---

## $state: Declaring Reactive State
[🔗 REPL](https://svelte-5-preview.vercel.app/#H4sIAAAAAAAACkWMwQqDMBBEfyUsPSgK7TmNQr9De7BxhdC4CcmmUEL-vRgPPc6beZNhMxYjyCkDLTuChIf30AN__RHiBy0j9BBdCvogKupgPI8zzWyRhXaJWAziEnlhbG7tfSZ1_Y9IvRKzI-FIW6PfQ25aMYyn13WlHtUmSpErLcfDaY3Qw-5WsxlcQXJIWJ7lB2vJQ9e1AAAA)
```js
<script>
	let count = $state(0);
</script>

<button onclick={() => count++}>
	clicks: {count}
</button>
```


<!-- Speaker notes:
• The first and most important rune is $state
• In this example 'count' becomes a reactive variable, initialized to 0,
  when 'count' changes, Svelte automaticly updates dependent UI parts -->

---

## $derived: Declaring Derived State

[🔗 REPL](https://svelte-5-preview.vercel.app/#H4sIAAAAAAAACkWNQQqDMBBFrxKGLrQKli6tCj1H7UKTEUJjEsxEKCF3L9HWLmf---8HmKRCB_UjgB5mhBru1kIJ9LbpcCsqQijBGb_w9GkcX6Slrtc9KSTGjdfEWnZyNBBml_z2S4Txo0KRMoGLXFFkO3xm10Q11V-lm9ETGc2M5kryVxuynLXdbi-KuM2FrzGm7s7vXduFDYzHpnTsoJvKdlDCbIScJAqoafEYn_EDTUmH7_wAAAA=)
```js
<script>
	let count = $state(0);
	let doubled = $derived(count * 2);
</script>

<button onclick={() => count++}>
	{doubled}
</button>

<p>{count} doubled is {doubled}</p>
```

- Expression should be side-effect free
- State changes not allowed inside derived expressions

<!-- Speaker notes:
$derived is used for computed values depending on other reactive state
• Example: 'doubled' always equals twice the value of 'count'
• Svelte auto-recomputes 'doubled' when 'count' changes
• It is important that $derived expressions should be pure, without side effects,
  that means the computed value should only depend on its inputs, 
  without modifying any external state or causing observable changes outside of its calculation. -->

---

## $effect: Running Side Effects

[🔗 REPL](https://svelte-5-preview.vercel.app/#H4sIAAAAAAAACj2OwQrCMAyGXyWEHSYO9Ty3gXjyGVRQaybFLhlrpkjpu0s38RBC_vB9ScDWOvJYHgPytSMscdf3WKB--jT4FzklLNDLOJiUVN4MttfmxACOFIyMrFBD5vWqlG8W27RJlVHbktE8X0DdQEgRgBH24mjl5JFf9hNrPbC8IQuTKl5mQ0ytWv-vnbi6jarCIGycNc86zOKJWi7j9NGBzUAdsZbw0yXJDDZYYCd321q6Y6nDSPEcv1yqukQBAQAA)
```js
<script>
  let count = $state(0);
  
  $effect(() => {
    console.log(`Count is now ${count}`);
  });
</script>

<button onclick={() => count++}>
  Increment: {count}
</button>
```

- Runs when component mounts and when dependencies change
- Used for side effects (e.g., logging, DOM updates outside Svelte)
- Automatically tracks dependencies

<!-- Speaker notes:
• $effect: Runs side effects when state changes
• this example prints out a new log  when count changes
• Runs on mount and after dependency changes -->

---

## Thank You!

Questions?

<!-- Speaker notes:
• Thank you for your attention!
• We've covered reactivity fundamentals in Svelte 5
• Open for questions on $state, $derived, $effect, or their use
• Happy to clarify or dive deeper into any topic discussed -->