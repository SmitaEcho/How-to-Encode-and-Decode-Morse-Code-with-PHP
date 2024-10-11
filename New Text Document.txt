<?php

// Morse code dictionary for encoding and decoding
$morse_Code = [
    'A' => '.-',    'B' => '-...',  'C' => '-.-.',  'D' => '-..',   'E' => '.',  
    'F' => '..-.',  'G' => '--.',   'H' => '....',  'I' => '..',    'J' => '.---', 
    'K' => '-.-',   'L' => '.-..',  'M' => '--',    'N' => '-.',    'O' => '---', 
    'P' => '.--.',  'Q' => '--.-',  'R' => '.-.',   'S' => '...',   'T' => '-',  
    'U' => '..-',   'V' => '...-',  'W' => '.--',   'X' => '-..-',  'Y' => '-.--', 
    'Z' => '--..',
    '0' => '-----', '1' => '.----', '2' => '..---', '3' => '...--', '4' => '....-', 
    '5' => '.....', '6' => '-....', '7' => '--...', '8' => '---..', '9' => '----.',
    ' ' => '/', // Using "/" for space between words in morse code
];

$morse_Code_Flip = array_flip($morse_Code);

function encode_To_Morse($text, $morse_Code) {
    $text = strtoupper($text);
    $encoded = [];
    foreach (str_split($text) as $char) {
        $encoded[] = $morse_Code[$char] ?? ''; // Encode only supported characters
    }
    return implode(' ', $encoded);
}

function decode_From_Morse($morse, $morse_Code_Flip) {
    $decoded = [];
    foreach (explode(' ', $morse) as $code) {
        $decoded[] = $morse_Code_Flip[$code] ?? ''; // Decode only supported Morse
    }
    return implode('', $decoded);
}

// Main logic to take input from user
echo "Enter text to encode or Morse code to decode: ";
$input = trim(fgets(STDIN)); // Get user input from command line

// Check if the input is morse code (it contains dots or dashes)
if (preg_match('/[.-]/', $input)) {
    // If input contains dots or dashes, decode from Morse
    echo "Decoded: " . decode_From_Morse($input, $morseCodeFlip) . "\n";
} else {
    
    echo "Encoded: " . encode_To_Morse($input, $morse_Code) . "\n";
}

?>
