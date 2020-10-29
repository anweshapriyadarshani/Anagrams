# Anagrams
Given a word W and a string S, find all starting indices in S which are anagrams of W.  For example, given that W is "ab", and S is "abxaba", return 0, 3, and 4.

const anagramOccurrencesOf = (w, s) => {
      const occurrencesCopy = [];
      let sCopy = s.slice(0);
    
      let index = 0;
      while (sCopy.length && index !== -1) {
        index = sCopy.indexOf(w);
        if (index === -1) { break; }
        occurrencesCopy.push((occurrencesCopy[occurrencesCopy.length - 1] + index + 1 || 0));
        sCopy = sCopy.slice(index + 1);
      }
      const occurrencesReverse = [];
      let sReverse = s.split('').reverse().join('');
    
      index = 0;
      while (sReverse.length && index !== -1) {
        index = sReverse.indexOf(w);
        if (index === -1) { break; }
        occurrencesReverse.push( (occurrencesReverse[occurrencesReverse.length - 1] - w.length - index + 1) || s.length - w.length);
        sReverse = sReverse.slice(index + 1);
      }
    
      return [...occurrencesCopy, ...occurrencesReverse].sort((a,b) => a -b);
    };
    
    console.log(anagramOccurrencesOf("ab", "abxaba"));
