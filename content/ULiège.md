[[To-Do]]
### Cours : 
---
#### Actif
[[Anglais]]
[[Rhétorique et sémiologie]]
[[Logique et analyse des raisonnements]]
[[Esthétique et philosophie de l’art]]
[[Introduction à l’histoire du Christianisme]]
[[Introduction à la métaphysique et à la théorie de la connaissance]]
[[Introduction à la philosophie contemporaine]]

#### Non-Actif
[[Atelier de pratique philosophie]]
[[Notions de critique historique]]
[[Philosophie de la citoyenneté 1]]
[[Philosophie des sciences humaines et pratiques de la philosophie, Cours Durabilité et transition]]
[[Histoire du Moyen-Âge]]
[[Introduction à l’éthique et à la philosophie morale]]
 
---


### Pages Autres : 
---
[[Read Like a Pro]]

---
```dataviewjs  
// Point de départ : ta note "05_MOC/ULiège.md"
const start = dv.page("05_MOC/MyAcademicKnowledge/ULiège");

// Ensemble pour éviter les doublons
let visited = new Set();
let toVisit = [start];
let results = [];

// Parcours récursif de tous les liens sortants
while (toVisit.length > 0) {
  const current = toVisit.pop();
  if (!current || visited.has(current.file.path)) continue;
  visited.add(current.file.path);
  results.push(current);

  // Trouver les notes liées (liens sortants)
  const outgoing = current.file.outlinks
    .map(l => dv.page(l.path))
    .filter(p => p);
  toVisit.push(...outgoing);
}

// Affiche un tableau cliquable de toutes les notes reliées
dv.table(["Notes liées (tous niveaux)"], results.map(r => [r.file.link]));
```