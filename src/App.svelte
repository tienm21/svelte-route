<script>
  import { Router, Route } from './router';
  import About from './pages/about.svelte';
  import Index from './pages/index.svelte';
  import NotFound from './pages/NotFound.svelte';
</script>

<ul>
  <li>
    <a href="/">Home</a>
  </li>
  <li>
    <a href="/about">About</a>
  </li>
  <li>
    <a href="/bar">Bar</a>
  </li>
</ul>

<!--  Setting Route -->
<Router hashbang={false}>
  <Route path="/">
    <Index />
  </Route>
  <Route path="/about">
    <About />
  </Route>
  <Route path="/*">
    <NotFound />
  </Route>
</Router>
