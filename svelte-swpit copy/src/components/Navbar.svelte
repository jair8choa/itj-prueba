<script>
  import { Router, Link, Route, navigate } from "svelte-routing";
  import { onMount } from "svelte";
  import { user } from "../stores/User";

  const cerrarsesion = () => {
    if (confirm("Deseas cerrar sesion")) {
      localStorage.clear()
      navigate('/', {replace: true})
    }
  };

  onMount(() => {
    document.querySelector(".toggle").onclick = function () {
      document.querySelector(".navigation-1").classList.toggle("active");
      document.querySelector(".main").classList.toggle("active");
    };

    function activeLink() {
      document
        .querySelectorAll(".navigation-1 li")
        .forEach((item) => item.classList.remove("hovered"));
      this.classList.add("hovered");
    }

    document.querySelectorAll(".navigation-1 li").forEach((item) => {
      item.addEventListener("mouseover", activeLink);
      item.addEventListener("click", activeLink);
    });
  });
</script>

<svelte:head />
<div class="navigation-1">
  <ul>
    <li>
      <a href="#">
        <span class="banner-img"> <img src="/svelte-swpit/imgs/halcon.png" alt="" /> </span>
      </a>
    </li>
    <li name="Home">
      <Link to="/home" replace={true}>
        <span class="icon"> <ion-icon name="home" /> </span>
        <span class="tittle">Inicio</span>
      </Link>
    </li>
    <li name="Encuestas">
      <Link to="/encuestas" replace={true}>
        <span class="icon"> <ion-icon name="document-text" /> </span>
        <span class="tittle">Encuestas</span>
      </Link>
    </li>
    <li>
      <a href="#" on:click={cerrarsesion}>
        <span class="icon"> <ion-icon name="log-out" /> </span>
        <span class="tittle">Cerrar Sesión</span>
      </a>
    </li>
  </ul>
</div>
