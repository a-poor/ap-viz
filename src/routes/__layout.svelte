<!-- src/routes/__layout.svelte -->
<div class="top-app-bar-container">
  <TopAppBar
    variant="static"
    color="primary"
  >
    <Row>
      <Section>
        <IconButton class="material-icons">menu</IconButton>
        <Title>AP-Viz</Title>
      </Section>
      <Section align="end" toolbar>
        <IconButton class="material-icons">file_download</IconButton>
        <IconButton class="material-icons">print</IconButton>
        <IconButton class="material-icons">bookmark</IconButton>
      </Section>
    </Row>
  </TopAppBar>
</div>

<script lang="ts">
  import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
  import IconButton from '@smui/icon-button';
</script>

<style>
  .top-app-bar-container {
    width: 100%;
    /* height: 320px; */
 
    overflow: auto;
    display: inline-block;
  }
 
  @media (max-width: 480px) {
    .top-app-bar-container {
      margin-right: 0;
    }
  }
 
  .app-body {
    padding: 0 10px;
  }
</style>

<div class="app-body">
  <slot></slot>
</div>
