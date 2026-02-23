---
layout: default
title: Arbol de familia
nav_order: 31
---

# Genealogia

<div id="FamilyChart" class="f3" style="width:100%;height:900px;margin:auto;background-color:rgb(33,33,33);color:#fff;"></div>
<script src="https://unpkg.com/d3@7"></script>
<script type="module" src="https://unpkg.com/family-chart@0.9.0"></script>
<link rel="stylesheet" href="https://unpkg.com/family-chart@0.9.0/dist/styles/family-chart.css">
<script type="module">

function create(data) {
  const f3Chart = f3.createChart('#FamilyChart', data)
    .setTransitionTime(1000)
    .setCardXSpacing(250)
    .setCardYSpacing(150)

  f3Chart.setCardHtml()
    .setCardDisplay([["name"],["nacimiento","juramento","defuncion"]])

  f3Chart.updateTree({initial: true})
}

const data = [
  {
    "id": "phantom_14",
    "data": {
      "gender": "M",
      "name": "14º Fantasma",
      "nacimiento": "1793",
      "defuncion": "1831"
    },
    "rels": {
      "spouses": ["marie_claire"],
      "children": ["phantom_15"]
    }
  },
  {
    "id": "marie_claire",
    "data": {
      "gender": "F",
      "name": "Marie Claire",
      "nota": "Pianista francesa",
      "defuncion": "1831"
    },
    "rels": {
      "spouses": ["phantom_14"],
      "children": ["phantom_15"]
    }
  },
  {
    "id": "phantom_15",
    "data": {
      "gender": "M",
      "name": "15º Fantasma",
      "nacimiento": "1812",
      "juramento": "1831",
      "defuncion": "1848"
    },
    "rels": {
      "parents": ["phantom_14", "marie_claire"],
      "spouses": ["juliet_adams"],
      "children": ["phantom_16"]
    }
  },
  {
    "id": "juliet_adams",
    "data": {
      "gender": "F",
      "name": "Juliet Adams",
      "alias": "Capitán Amazona"
    },
    "rels": {
      "spouses": ["phantom_15"],
      "children": ["phantom_16"]
    }
  },
  {
    "id": "phantom_16",
    "data": {
      "gender": "M",
      "name": "16º Fantasma",
      "nacimiento": "1831",
      "juramento": "1848",
      "defuncion": "1869"
    },
    "rels": {
      "parents": ["phantom_15", "juliet_adams"],
      "spouses": ["asta_jensen", "annie_morgan"],
      "children": ["phantom_17", "julia_walker"]
    }
  },
  {
    "id": "asta_jensen",
    "data": {
      "gender": "F",
      "name": "Asta Jensen",
      "defuncion": "1848",
      "nota": "Fallecida por fiebres el mismo año de la boda"
    },
    "rels": {
      "spouses": ["phantom_16"]
    }
  },
  {
    "id": "annie_morgan",
    "data": {
      "gender": "F",
      "name": "Annie Morgan",
      "origen": "Texas, EE.UU."
    },
    "rels": {
      "spouses": ["phantom_16"],
      "children": ["phantom_17", "julia_walker"]
    }
  },
  {
    "id": "phantom_17",
    "data": {
      "gender": "M",
      "name": "17º Fantasma",
      "nacimiento": "1852",
      "juramento": "1870",
      "defuncion": "1889"
    },
    "rels": {
      "parents": ["phantom_16", "annie_morgan"],
      "spouses": ["mary_stillwell", "kate_somerset"],
      "children": ["phantom_18", "christopher_somerset"]
    }
  },
  {
    "id": "julia_walker",
    "data": {
      "gender": "F",
      "name": "Julia Walker",
      "nacimiento": "1852",
      "rol": "La Mujer Enmascarada (temporal)"
    },
    "rels": {
      "parents": ["phantom_16", "annie_morgan"],
      "spouses": ["paul_colbert"]
    }
  },
  {
    "id": "paul_colbert",
    "data": {
      "gender": "M",
      "name": "Paul Colbert",
      "profesion": "Médico"
    },
    "rels": {
      "spouses": ["julia_walker"]
    }
  },
  {
    "id": "mary_stillwell",
    "data": {
      "gender": "F",
      "name": "Mary Stillwell",
      "origen": "Boston, EE.UU."
    },
    "rels": {
      "spouses": ["phantom_17"],
      "children": ["phantom_18"]
    }
  },
  {
    "id": "kate_somerset",
    "data": {
      "gender": "F",
      "name": "Kate Somerset",
      "nota": "Relación extramatrimonial (1869)"
    },
    "rels": {
      "spouses": ["phantom_17"],
      "children": ["christopher_somerset"]
    }
  },
  {
    "id": "phantom_18",
    "data": {
      "gender": "M",
      "name": "18º Fantasma (Kit)",
      "nacimiento": "1871",
      "juramento": "1889"
    },
    "rels": {
      "parents": ["phantom_17", "mary_stillwell"]
    }
  },
  {
    "id": "christopher_somerset",
    "data": {
      "gender": "M",
      "name": "Christopher Somerset",
      "parentesco": "Hijo ilegítimo"
    },
    "rels": {
      "parents": ["phantom_17", "kate_somerset"]
    }
  }
];

create(data);

</script>