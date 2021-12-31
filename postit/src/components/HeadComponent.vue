<template>
  <body>
    <header class="header">
      <div class="center">
        <div id="logo">
          <img src="../assets/sticky.png" alt="" />
          <span id="brand">
            <strong>PoSt-It</strong>
          </span>
        </div>
        <!-- MENu-->
        <nav id="menu">
          <ul>
            <li>
              <router-link active-class="active" to="/">HOME</router-link>
            </li>
            <li>
              <router-link active-class="active" to="/Newposit">NEW PoSt-It</router-link>
            </li>
          </ul>
        </nav>
        <div class="clearfix"></div>
      </div>
    </header>
  </body>
</template>
<script>
export default {
  name: "HeadComponent",
};
</script>