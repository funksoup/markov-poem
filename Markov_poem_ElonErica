// Markov Chain Poem

// text = Elon Musk's twitter feed + Erica Jong's erotic poem 'Climbing You' 

var text = "First firing of Starship Raptor flight engine! So proud of great work by @SpaceX team!! At @SpaceX Texas with engineering team getting ready to fire new Raptor rocket engine. Only a matter of time. looks like sentient choc ice cream. Initially making one 200 metric ton thrust engine common across ship & booster to reach the moon as fast as possible. Preparing to fire the Starship Raptor engine at @SpaceX. All our patent are belong to you. Our true competition is not the small trickle of non-Tesla electric cars being produced, but rather the enormous flood of gasoline cars pouring out of the world’s factories every day. Exciting to see all the new electric vehicles coming to market! We created Tesla to accelerate a sustainable future & it’s happening! I want to understand the steep thing that climbs ladders in your throat. I can't make sense of you. Everywhere I look you're there -- a vast landmark, a volcano poking its head through the clouds, Gulliver sprawled across Lilliput. I climb into your eyes, looking. The pupils are black painted stage flats. They can be pulled down like window shades. I switch on a light in your iris. Your brain ticks like a bomb. In your offhand, mocking way you've invited me into your chest. Inside: the blur that poses as your heart. I'm supposed to go in with a torch or maybe hot water bottles & defrost it by hand as one defrosts an old refrigerator. It will shudder & sigh (the icebox to the insomniac). Oh there's nothing like love between us. You're the mountain, I am climbing you. If I fall, you won't be all to blame, but you'll wait years maybe for the next doomed expedition. ";


//Function that converts string to an array of all lower-case words with no punctuation
function parseText(str) {
  var removePunc = /[1234567890.,\/#!$%\^&\*;:{}=\-_`~()@+?><[\]+]/gi;
  
  var wordArray = str.replace(removePunc, "").toLowerCase().split(" ");
  return wordArray;
}


//Function that creates Markov Chain object from word array
function generateWordPairs(str) {
  var wordArray = parseText(str);
  var markovChain = {};
  
  for (var i=0; i<wordArray.length-1; i++) {
    var word = wordArray[i];
    var nextWord = wordArray[i+1];
    
    if (markovChain[word]) { 
      markovChain[word].push(nextWord);
    }
    else markovChain[word] = [nextWord];
  }
  return markovChain;

}

var markovChain = generateWordPairs(text);
// console.log(markovChain);


// Markov representation of text array

function getsRandomWord(randWord, markovChain) {
var arrKeys = markovChain[randWord];
  if (arrKeys === undefined){
    return "try again";
  }
var lenArray = arrKeys.length 
var nextRandWord = markovChain[randWord][getsRandomInt(0, lenArray)];
return nextRandWord;
}

function getsRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min; // the maximum is exclusive and the minimum is inclusive
}
 

function writeLine(markovChain, num, initialWord){
  var ourKeys = Object.keys(markovChain);
  if (Object.keys(markovChain).indexOf(initialWord) === -1){
    lenArray = ourKeys.length;
    initialWord = ourKeys[getsRandomInt(0, lenArray)];
  }
  var newStr = initialWord + " ";
  var temp = initialWord;
  var i = 0;
  while (i < num - 1){
    if (temp !== "try again"){
      var newWord = getsRandomWord(temp, markovChain);
      newStr += newWord + " ";
      temp = newWord;
      i++;
    }
  } 
  return newStr;
}


function makePoem(initialWord, numWords, numLines){
  var poem = "";
  var temp = initialWord;
  for (var i = 0; i < numLines; i++){
    var line = writeLine(markovChain, numWords, temp);
    var words = line.split(" ");
    var endWord = words[words.length-2] //because they start with a space
    temp = writeLine(markovChain, numWords, endWord).split(" ")[1];
    poem += line + "\n";
  }
  console.log("Elon Musk's musings mixed with Erica Jong's erotic poetry");
  console.log(poem);
}

makePoem("doomed expedition", 4, 5);



