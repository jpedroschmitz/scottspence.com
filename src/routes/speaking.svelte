<script context="module">
  export const load = async () => {
    try {
      const Copy = await import(`../../copy/speaking.md`)
      return {
        props: {
          Copy: Copy.default,
        },
      }
    } catch (e) {
      return {
        status: 404,
        error: 'Uh oh!',
      }
    }
  }
</script>

<script>
  import Head from '$lib/components/head.svelte'
  import { name, website } from '$lib/info'
  import { ogImageUrl } from '$lib/og-image-url-build'

  export let Copy
</script>

<Head
  title={`Speaking · ${name}`}
  description={`A list of events where ${name} has held a workshop, a talk or spoken publically.`}
  image={ogImageUrl(name, `scottspence.com`, `Scott Speaks!`)}
  url={`${website}/speaking`}
/>

<div class="all-prose">
  <svelte:component this={Copy} />
</div>

<div class="flex flex-col w-full my-10">
  <div class="divider" />
</div>
