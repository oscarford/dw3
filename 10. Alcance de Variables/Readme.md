# Alcance de variables

Analizar el alcance de las variables según el siguiente *.scss y el css que genera

```
// Colores
$c-tit: #666; // Define variable global
$c-fon: lavender; // Define variable global
$c-tex: #333; // Define variable global

@mixin hero(){
	background-color:$c-fon; // Lee variable global
	color:$c-tex; // Lee variable global
	h1{
		color:$c-tit; // Lee variable global
	}
}

.hero {
    @include hero();
}
.hero-dark {
    $c-tit: #fefefe !global; // Sobre-escribe variable global
    $c-fon: #333 !global; // Sobre-escribe variable global
    $c-tex: #FF0; // Define variable local
    @include hero();
}

h1{
    $c-tit-alt:#999; // Define variable local
    color:$c-tit-alt; // Lee variable local
}

body{
    background:$c-fon; // Lee variable global
    color:$c-tex; // Lee variable global
    //border-color:$c-tit-alt; // Variable no definida
}

```