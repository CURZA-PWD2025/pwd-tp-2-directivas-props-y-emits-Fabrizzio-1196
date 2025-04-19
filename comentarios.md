## Comentarios

Fabrizio vas por buen camino pero veo que tenes algunos errores importantes que paso a detallar
- La idea es usar emit para capturar eventos del hijo y poder pasar data al padre, de la manera que lo pensaste no lo estas haciendo
- El ``CardComponente`` deberia mostrar cada pelicula, pero lo estas usando como con **CardList** donde con un contenedor ``div`` estas renderizando la info con un ``v-for``
  y eso no seria correcto, la idea es que el componente reciba del padre una pelicula en este caso el mismo seria ``App.vue``
  te invito a que lo corregias y reenvies.
- No estas usando v-if si la portada no existe.
