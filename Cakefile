# Requires coffee-script and uglifyjs

{ exec, spawn } = require 'child_process'
src = 'highlight-permalinked-comment'

task 'build', 'compile and minify', ->
	exec "coffee -c #{src}.coffee && uglifyjs #{src}.js -cm -o #{src}.min.js"
