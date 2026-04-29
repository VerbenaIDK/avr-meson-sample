project('avr-sample', 'c',
  version : '20260429_v002',
  default_options : ['buildtype=minsize'])

# Includes and subdirs
includes = include_directories('lib')
subdir('src')

# avrdude
programmer = 'urclock'
processor = 'atmega328pb'
port = '/dev/ttyUSB0'
memory = 'flash'

# Compile args
arguments = []
add_project_arguments(arguments, language : 'c')

# Executbles
firmware = executable('firmware.elf', 
  sources,
  include_directories : includes) # builds the firmware

# Targets

## flash firmware, build if necessary
flash_firmware = run_target('flash',
  command : ['avrdude', '-c', programmer, 
  '-p', processor,
  '-P', port,
  '-U',
  ':'.join([ memory, 
    'w', firmware.name() ]) ], # hacky looking, but works 
  depends : [firmware])
