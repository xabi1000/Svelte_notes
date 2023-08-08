Además de `createEventDispatcher`, Svelte ofrece otra opción para manejar la comunicación entre componentes: la asignación de propiedades y eventos. Aquí te muestro cómo puedes usar asignación de propiedades y eventos para lograr el mismo objetivo que mencionaste:

**Componente Padre (App.svelte):**

```svelte
<script>
  import OuterComponent from './OuterComponent.svelte';
  let inputValue1 = '';
  let inputValue2 = '';
</script>

<OuterComponent bind:value1={inputValue1} bind:value2={inputValue2} />
<p>Valor del primer input en el componente padre: {inputValue1}</p>
<p>Valor del segundo input en el componente padre: {inputValue2}</p>
```

**Componente Intermedio (OuterComponent.svelte):**

```svelte
<script>
  import InnerComponent from './InnerComponent.svelte';
  let value1 = '';
  let value2 = '';
</script>

<InnerComponent bind:value1={value1} bind:value2={value2} />
```

**Componente Interno (InnerComponent.svelte):**

```svelte
<script>
  export let value1;
  export let value2;
</script>

<input type="text" bind:value={value1} />
<input type="text" bind:value={value2} />
```

En este enfoque, los valores de los inputs se pasan directamente a través de la asignación de propiedades. Cada componente intermedio y el componente padre tienen acceso directo a los valores de los inputs y cualquier cambio se reflejará en todos los niveles. No es necesario utilizar `createEventDispatcher` en este caso, ya que la asignación de propiedades y eventos de Svelte manejará la actualización automáticamente.

Ambos enfoques tienen sus ventajas y desventajas. La elección entre ellos depende del caso de uso y la estructura de tu aplicación.