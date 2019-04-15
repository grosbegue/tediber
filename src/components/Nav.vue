<template>
  <nav>
    <div class="halfNav">
      <img class="marque" src="../../public/Logo_tediber.png">

      <li>NOS PRODUITS</li>
      <li>LE CONCEPT</li>
      <li>AVIS</li>
    </div>

    <img class="ours" src="../../public/ours.png">

    <div class="halfNav R">
      <li>PUB TV</li>
      <li>BLOG</li>
      <li>MON COMPTE</li>
      <li>01 86 95 47 10</li>

      <img class="panier" src="../../public/panier.svg">
    </div>
  </nav>
</template>









<script>
export default {
  name: "Nav"
};
</script>


<style scoped>
.marque {
  height: 50px;
  margin-right: 10px;
}

nav {
  padding: 3px 5px 0px 5px;
  display: flex;
  flex-direction: row;
  align-items: stretch;
  justify-content: space-between;
}

.halfNav {
  display: flex;
  flex-direction: row;
  width: 40%;
}

.R {
  justify-content: flex-end;
}

li {
  list-style-type: none;
  height: 30px;
  padding: 15px 10px 5px 10px;
  font-size: 0.8em;
}

.ours {
  height: 50px;
}

.panier {
  height: 47px;
}
</style>