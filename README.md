# _sus-hib-off-WindowsOS_

```python
#!/usr/bin/env python
#Windows 0S
#API Windows - Función SetSuspendState/CreateWaitableTimer/SetWaitableTimer

"""
from ctypes import windll
# Suspender.
if not windll.powrprof.SetSuspendState(False, False, False):
    print("No se ha podido suspender el sistema.")
"""
#El primer argumento de la función determina si el sistema debe ingresar en estado de suspensión (False) o hibernación (True).
"""
# Hibernar.
if not windll.powrprof.SetSuspendState(True, False, False):
    print("No se ha podido suspender el sistema.")
"""
from ctypes import windll, byref
from ctypes.wintypes import LARGE_INTEGER
timer = windll.kernel32.CreateWaitableTimerW(None, True, None)
if timer:
    # Suspender y despertar luego de 10 segundos.
    if windll.kernel32.SetWaitableTimer(timer,
        byref(LARGE_INTEGER(-100000000)), 0, None, None, True):
        if not windll.powrprof.SetSuspendState(False, False, False):
            print("No se ha podido suspender el sistema.")
    else:
        print("No se pudo crear el timer.")

```
