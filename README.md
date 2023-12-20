
def control_motor(direction, speed):
    if direction:
        in1.value(0)
        in2.value(1)
        in3.value(0)
        in4.value(1)
    else:
        in1.value(1)
        in2.value(1)
        in3.value(1)
        in4.value(1)
    pwm.duty(speed)
        
def motores_ambidiestros(direction, speed):
    if direction:
        in1.value(0)
        in2.value(1)
        in3.value(0)
        in4.value(1)
    else:
        in1.value(1)
        in2.value(0)
        in3.value(0)
        in4.value(1)
    pwm.duty(speed)

while True:

        distance = sensor.distance_cm()
        print("Distancia: {} cm".format(distance))
        
        if distance >= 15:
            print("Avanzar")
            control_motor(direction=False, speed=1023)

        else:
            print("Retroceder")
            control_motor(direction=True, speed=1023)
            time.sleep(0.5) # Espera 1 segundo para retroceder
            print("Girar")
            motores_ambidiestros(direction=True, speed=1023)
            time.sleep(0.2)# Espera 1 segundo para girar
            
        time.sleep(0.05) # Espera 1 segundo antes de la siguiente lecturas
from machine import Pin, PWM
import time
from hcsr04 import HCSR04

trig_pin = 10  # Pin de trigger para el sensor HC-SR04
echo_pin = 9  # Pin de echo para el sensor HC-SR04

# Configuración del sensor HC-SR04
sensor = HCSR04(trigger_pin=10, echo_pin=9)

# Pines para el control de dirección y velocidad
in1 = Pin(5, Pin.OUT) # D1
in2 = Pin(4, Pin.OUT) # D2
in3 = Pin(0, Pin.OUT) # D3
in4 = Pin(2, Pin.OUT) # D4
pwm = PWM(Pin(13,12), freq=1000) # D7, solo si se quiere controlar vel.

def control_motor(direction, speed):
    if direction:
        in1.value(0)
        in2.value(1)
        in3.value(0)
        in4.value(1)
    else:
        in1.value(1)
        in2.value(1)
        in3.value(1)
        in4.value(1)
    pwm.duty(speed)
        
def motores_ambidiestros(direction, speed):
    if direction:
        in1.value(0)
        in2.value(1)
        in3.value(0)
        in4.value(1)
    else:
        in1.value(1)
        in2.value(0)
        in3.value(0)
        in4.value(1)
    pwm.duty(speed)

while True:

        distance = sensor.distance_cm()
        print("Distancia: {} cm".format(distance))
        
        if distance >= 15:
            print("Avanzar")
            control_motor(direction=False, speed=1023)

        else:
            print("Retroceder")
            control_motor(direction=True, speed=1023)
            time.sleep(0.5) # Espera 1 segundo para retroceder
            print("Girar")
            motores_ambidiestros(direction=True, speed=1023)
            time.sleep(0.2)# Espera 1 segundo para girar
            
        time.sleep(0.05) # Espera 1 segundo antes de la siguiente lecturas
