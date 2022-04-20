<script>
  import { Router, Route } from './router';
  import About from './pages/about.svelte';
  import Index from './pages/index.svelte';
  import NotFound from './pages/NotFound.svelte';
  import { onMount } from 'svelte';
  import Users from './pages/users.svelte';
  import Userdetail from './pages/userdetail.svelte';
  import list from './store/store';
  import SvelteSeo from 'svelte-seo';

  onMount(() => {
    window.onbeforeunload = () => localStorage.clear();
    list.set([]);
  });
</script>

<SvelteSeo
  title="My Simple Svelte App"
  description="A short description goes here. Hello Xin Chào Mọi Người đây là một web  mình code bằng svelte ahihihi"
  openGraph={{
    title: 'Open Graph Title',
    description: 'Open Graph Description',
    url: 'https://www.example.com/page',
    type: 'website',
    images: [
      {
        url: 'https://scontent.fhan4-2.fna.fbcdn.net/v/t1.6435-9/150150991_479446133057110_927264625403946655_n.jpg?_nc_cat=111&ccb=1-5&_nc_sid=09cbfe&_nc_ohc=DBjhdSslfKAAX_HGMOr&_nc_ht=scontent.fhan4-2.fna&oh=00_AT8lotzVvgsLdDCksTtUJ7s5X9MypGE_yfhAJNlgG-l1Yw&oe=628741D8',
        width: 850,
        height: 650,
        alt: 'Og Image Alt',
      },
    ],
  }} />

<ul>
  <li>
    <a href="/">Home</a>
  </li>
  <li>
    <a href="/users">Users</a>
  </li>
  <li>
    <a href="/about">About</a>
  </li>
</ul>

<!--  Setting Route -->
<div class="container">
  <main>
    <Router hashbang={false}>
      <Route path="/">
        <Index />
      </Route>
      <Route path="/about">
        <About />
      </Route>
      <Route path="/users">
        <Users />
      </Route>
      <Route path="/users/:id" let:id>
        <Userdetail {id} />
      </Route>
      <Route path="/*">
        <NotFound />
      </Route>
    </Router>
  </main>
  <footer>
    <hr />
    <p style="padding-top:20px ;">
      Copyright &copy; 2017 All Rights Reserved by
      <a href="#/">Scanfcode</a>.
    </p>
  </footer>
</div>

<style>
  .container {
    padding: 20px;
  }
  main {
    min-height: 350px;
  }
  footer {
    margin-top: 20px;
  }
  ul {
    display: flex;
    background-color: #5f8aff;
    color: #fff;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  }
  li a {
    padding: 10px 20px;
    display: block;
    color: #fff;
  }
  li a:hover {
    background-color: #4870e0;
  }
</style>
