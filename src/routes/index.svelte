<script context="module">
    export async function preload() {
        let data = {};
        const response = await this.fetch(
            `https://us-central1-pugstagram-co.cloudfunctions.net/data`,
        );
        data = await response.json();
        return { data };
    };
</script>

<script>
    import Main from '../components/Main.svelte';
    import Timeline from '../components/Timeline.svelte';
    import Sidebar from '../components/Sidebar.svelte';
    export let data;
</script>

<svelte:head>
    <title>Pugstagram</title>
</svelte:head>

<Main>
    <Timeline posts={data.posts} />
    <Sidebar {...data.user} />
</Main>