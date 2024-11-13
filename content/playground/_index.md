+++
title = "Playground"
template = "index.html"
+++

Playground

<textarea cols="80" rows="20">
# Define a namespace
(ns my\example)

# Define a variable with name "my-name" and value "world"
(def my-name "world")

# Define a function with name "print-name" and one argument "your-name"
(defn print-name [your-name]
(print "hello" your-name))

# Call the function
(print-name my-name)
</textarea>
<button>Run</button> 
<h2>Result</h2>
<div id="result"> </div>

<script>
(async () => {
  const { PhpWeb } = await import('https://cdn.jsdelivr.net/npm/php-wasm@0.0.9-alpha-20/PhpWeb.mjs');

const sharedLibs = [];

const files = [
    {
        name: 'test.php',
        parent: '/',
        url: 'test.txt'
    }
];

const php = new PhpWeb({sharedLibs, files});

  //const php = new PhpWeb;
  //const input  = document.querySelector('#date-input');
  //const format = document.querySelector('#date-format');
  //const output = document.querySelector('#date-output');

  // Return an actual PHP function to Javascript:
  //const phpStrtotime = await php.x`strtotime(...)`;
  //const phpDate = await php.x`date(...)`;

  //const formatTime = (format, time) => phpDate(format, phpStrtotime(time));

  //input.addEventListener('input', () => output.innerText = formatTime(format.value, input.value));
  //format.addEventListener('input', () => output.innerText = formatTime(format.value, input.value));

  //format.value = 'Y-m-d H:i:s';
  //input.value = '8:00pm 2 days ago';

  //output.innerText = formatTime(format.value, input.value);

    php.addEventListener('output', (event) => console.log(event.detail));
    php.addEventListener('error',  (event) => console.log(event.detail));
    const exitCode = await php.run('<?php require "test.php";');
})();
</script>