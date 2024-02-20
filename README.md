function lireSyllabes(phrase) {
  // Découper la phrase en mots
  const mots = phrase.split(" ");

  // Liste pour stocker les syllabes
  const syllabes = [];

  // Parcourir chaque mot
  for (const mot of mots) {
    // Découper le mot en syllabes
    const syllabesMot = [];
    const voyelles = "aeiouy";
    for (let i = 0; i < mot.length; i++) {
      // Si la lettre est une voyelle
      if (voyelles.includes(mot[i])) {
        // Si la lettre est la première du mot ou si la lettre précédente est une consonne
        if (i === 0 || !voyelles.includes(mot[i - 1])) {
          syllabesMot.push(mot.slice(i));
          break;
        }
      }
      // Si la lettre est une consonne
      else {
        // Si la lettre est la dernière du mot
        if (i === mot.length - 1) {
          syllabesMot.push(mot.slice(i));
        }
        // Si la lettre suivante est une voyelle
        else if (voyelles.includes(mot[i + 1])) {
          syllabesMot.push(mot.slice(i, i + 2));
        }
      }
    }

    // Ajouter les syllabes du mot à la liste générale
    syllabes.push(...syllabesMot);
  }

  return syllabes;
}

// Exemple d'utilisation
const phrase = "Bonjour, comment allez-vous ?";
const syllabes = lireSyllabes(phrase);

// Afficher les syllabes
console.log(syllabes);
