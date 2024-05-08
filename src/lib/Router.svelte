<script context="module">
import Home from '../pages/Home.svelte';
import Settings from '../pages/Settings.svelte';
import Account from '../pages/Account.svelte';
import Page404 from '../pages/404.svelte';
import { writable, get } from 'svelte/store';

// Define routes here after importing above
let routes = {
    '/': Home,
    '/settings': Settings,
    '/accounts': Account,
}

// Our default route when we load our router into the app
let currentRoute = writable(routes[window.location.pathname] || Home);

// I don't think this is needed
// TODO: Remove this later
function init () {
    window.onpopstate = () => {
        console.log('popstate detected');
    }
}


function navigateTo (url) {
    let currentUrl = window.location.pathname;
    console.log(`navigating from ${url} > ${currentUrl}`);
    if(url === currentUrl) {
        console.log('Same route detected, aborting navigation.'); 
        return;
    }
    window.history.pushState({page: `${url}`}, "", url);
    updatePage(url);
}

function updatePage (url) {
    console.log(`updating page to ${url}`);
    currentRoute.set(routes[url] || Page404);
}

export { navigateTo, init };

</script>

<script>

let routeToLoad = get(currentRoute);

currentRoute.subscribe((value) => {
    console.log('current route changed', window.location.pathname);
    routeToLoad = value;
});


</script>

<main>
    <svelte:component this={routeToLoad} />
</main>
