Import('RTT_ROOT')
import os
from building import * 

# get current dir path
cwd = GetCurrentDir()

# init src and inc vars
src = []
inc = []

# add libyaml common include
inc += [cwd + '/src']
inc += [cwd + '/include']

# add libyaml basic code
src += Glob('src/*.c')

# add group to IDE project
objs = DefineGroup('libyaml-0.2.5', src, depend = ['PKG_USING_LIBYAML'], CPPPATH = inc)

# traversal subscript
list = os.listdir(cwd)
if GetDepend('PKG_USING_LIBYAML'):
    for d in list:
        path = os.path.join(cwd, d)
        if os.path.isfile(os.path.join(path, 'SConscript')):
            objs = objs + SConscript(os.path.join(d, 'SConscript'))

Return('objs') 
