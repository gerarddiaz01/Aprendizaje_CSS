Here are the CSS selectors for each exercise:

1.  **Selecciona los elementos div que sean hijos de otro div**
    `div div`

2.  **Selecciona el último elemento de un grupo de elementos hermanos li**
    `li:last-child`

3.  **Selecciona los hijos pares de un elemento li**
    `li:nth-child(even)`

4.  **Selecciona los hijos impares de un elemento li**
    `li:nth-child(odd)`

5.  **Selecciona los elementos p que sean hijos de article**
    `article > p`

6.  **Selecciona los p que esten dentro de un article**
    `article p`

7.  **Selecciona los titulos principal h1 y los h3**
    `h1, h3`

8.  **Selecciona los ol que esten dentro de body**
    `body ol`

9.  **Los elementos <ul> que sean hijos de <body>**
    `body > ul`

10. **Los elementos <a> que sean hijos de <p>**
    `p > a`

11. **Los elementos <div> que sean descendientes de <body>**
    `body div`

12. **El primer hijo de body**
    `body :first-child`

13. **El último hijo de <ul>**
    `ul :last-child`

14. **El primer hijo de <ul>**
    `ul :first-child`

15. **Los elementos <li> pares de <ul>**
    `ul li:nth-child(even)`

16. **Los elementos <li> impares de <ul>**
    `ul li:nth-child(odd)`

17. **El hijo de <ul> que esté en la posición 3**
    `ul :nth-child(3)`

18. **Un párrafo con la identificación "platano".**
    `p#platano`

19. **Un elemento con la clase "rojo" que sea primer hijo.**
    `.rojo:first-child`

20. **Seleccionar los h2 dentro de un section**
    `section h2`

21. **Seleccionar el segundo hijo de un elemento section**
    `section :nth-child(2)`

22. **Seleccionar los hijos pares de un elemento ol**
    `ol :nth-child(even)`

23. **Seleccionar el antepenúltimo li de un ul de longitud indefinida**
    `ul li:nth-last-child(2)`

24. **Seleccionar los p, que tengan la clase verde y que sean hijos directos de un div**
    `div > p.verde`

25. **Seleccionar los a que sean hijos de div y tengan un atributo class que contenga la palabra grande**
    `div > a[class*="grande"]`

26. **Los button que sean hijos de un section**
    `section > button`

27. **Los button que sean hijos únicos**
    `button:only-child`

28. **Los span que sean primeros hijos de un p**
    `p > span:first-child`

29. **Los input que vayan a continuación de un label y además sean hijos de un section**
    `section > label + input`

30. **Los button que tengan como padre un div**
    `div > button`

31. **Penúltimo hijo de body**
    `body :nth-last-child(2)`

32. **Todos los label con el atributo for="mascota"**
    `label[for="mascota"]`

33. **Todos los elementos "img" que tengan la clase "clasec", y que se encuentren dentro de cualquier elemento "div".**
    `div img.clasec`

34. **Todos los enlaces dentro de párrafos.**
    `p a`

35. **Todos los elementos que tengan la clase "Curvado".**
    `.Curvado`

36. **Todos los elementos a y ol que tengan la clase "Recto".**
    `a.Recto, ol.Recto`

37. **Todos los elementos "a" que se encuentren dentro de cualquier elemento "h2", que a su vez se encuentren dentro de cualquier elemento "div".**
    `div h2 a`

38. **Todos los hijos de span que estén dentro de un p que estén dentro de un div.**
    `div p span *`

39. **Todos los elementos "p" y todos los elementos con atributo class="aviso" que estén dentro de div.**
    `div p, div .aviso`

40. **Los elementos "em" y "a" que sean hijos directos de elementos "p", cuyo id sea "Sons".**
    `p#Sons > em, p#Sons > a`

41. **Todos los elementos a contenidos en .basico**
    `.basico a`

42. **Todos los "h2" dentro de una clase.lolito**
    `.lolito h2`

43. **Todos los elementos dentro de un <p>**
    `p *`

44. **El selector que está dentro de un párrafo que a su vez está dentro de un div**
    `div p *`

45. **Seleccionar un <span> que sea hijo directo de un <p>**
    `p > span`

46. **Seleccionar un <li> dentro de un <p> dentro de un <h1>**
    `h1 p li`

47. **Seleccionar todos los <div> que tienen la clase .transbox**
    `div.transbox`

48. **Todos los <p> que estan dentro de cualquier <h1>**
    `h1 p`

49. **Todos los <li>**
    `li`

50. **Todos los <p> que son hijos de un <h2>**
    `h2 > p`

51. **Todos los párrafos dentro de un div.**
    `div p`

52. **Todos los elementos a de la pagina**
    `a`

53. **Todos los elementos dentro de la clase.libreConf**
    `.libreConf *`

54. **todos los p dentro de la clase.libreConf**
    `.libreConf p`

55. **todos los p dentro de h2 dentro de div**
    `div h2 p`

56. **todos los p contenidos en el id prueba1**
    `#prueba1 p`

57. **todos los a que sean hijos de un p y que a su vez se encuentren dentro de un div**
    `div p > a`

58. **todos los h1, h2 y h3 que tengan la clase.libreConf**
    `h1.libreConf, h2.libreConf, h3.libreConf`

59. **seleccionar el elemento p cuyo id sea párrafo1**
    `p#parrafo1`

60. **todos los a que sean hijos directos de p cuya id sea hijos**
    `p#hijos > a`

61. **Todos los "p" que estén dentro de un "div"**
    `div p`

62. **Los dos primeros "p"**
    `p:nth-child(-n+2)` or `p:first-of-type, p:nth-of-type(2)`

63. **Todos los elementos "a" que tengan la clase "azul" que estén dentro de un "div" que contenga la id "primero"**
    `div#primero a.azul`

64. **Todos los elementos "span" y todos los elementos "div" que tengan la clase "holaktal"**
    `span.holaktal, div.holaktal`

65. **Todos los elementos "li" con el atributo "h3" dentro de los "p" que sean hijos directos de "div"**
    `div > p li[h3]`

66. **Todos los elementos impares de un "p"**
    `p :nth-child(odd)`