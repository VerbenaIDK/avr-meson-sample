project('avr-sample', 'c',
  version : 'v0.1',
  default_options : ['buildtype=minsize'])

includes = include_directories('lib')

subdir('src')

# avrdude
programmer = 'urclock'
processor = 'atmega328pb'
port = '/dev/ttyUSB0'

arguments = []
add_project_arguments(arguments, language : 'c')

firmware = executable('firmware.elf', 
  sources,
  include_directories : includes)

run_target('flash',
  command : ['avrdude', '-c', programmer, 
  '-p', processor,
  '-P', port,
  '-U', 'flash:w:firmware.elf:e']) # file to flash
