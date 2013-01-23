# Requires coffee-script and uglifyjs

{ exec, spawn } = require 'child_process'
fs = require 'fs'

# Use first CoffeeScript file
src    = ( file.replace /\.coffee$/, '' for file in fs.readdirSync('.') when file.match(/coffee$/) ).pop()
date   = new Date().toDateString()
banner = """
/*!
* Highlight Permalinked Comment
* Copyright (c) 2012 Evan Solomon #{date}
* Licensed GPL
*/
"""

prependBanner = ( targetFile ) ->
	fs.readFile targetFile, 'utf-8', ( err, code ) ->
		return if err
		fs.writeFile targetFile, "#{banner}\n#{code}"

task 'build', 'compile and minify', ->
	exec "coffee -c #{src}.coffee && uglifyjs #{src}.js -cm -o #{src}.min.js", ->
		for ext in [ 'js', 'min.js' ]
			targetFile = "#{src}.#{ext}"
			prependBanner targetFile if fs.existsSync targetFile
