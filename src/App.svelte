<script>
  // @ts-ignore
  import { Route, Router, Link } from "svelte-routing";
  let basepath = "/";

  import Login from './Login.svelte'
  import Admin from './Admin.svelte'

  import IssueCard from './IssueCard.svelte'
  import GetValueOfCard from "./GetValueOfCard.svelte";
  import SetValueOfCard from "./SetValueOfCard.svelte";
</script>

<Router {basepath}>
    <Route path="/">
      <Login></Login>
    </Route>

    <Route path="/admin-panel/dashboard/">
      <Admin></Admin>
    </Route>

    <Route path="/admin-panel/">
      <Admin></Admin>
    </Route>

    <Route path="/admin-panel/issuecard/">
      <IssueCard></IssueCard>
    </Route>

    <Route path="/admin-panel/value/get">
      <GetValueOfCard></GetValueOfCard>
    </Route>

    <Route path="/admin-panel/value/set">
      <SetValueOfCard></SetValueOfCard>
    </Route>
</Router>