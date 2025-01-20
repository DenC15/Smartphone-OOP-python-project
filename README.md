# Auto engine OOP python project
class Engine:
    def __init__(self):
        self.running = False

    def turn_on(self):
        self.running = True

    def turn_off(self):
        self.running = False

    def get_running_state(self):
        return self.running


class FuelTank:
    def __init__(self, capacity):
        self.capacity = capacity
        self.current_level = 0.0

    def fill_up(self, amount_fuel):
        if amount_fuel <= 0:
            print("Fuel amount cannot be zero or negative")
            return
        self.current_level = min(self.capacity, self.current_level + amount_fuel)

    def get_capacity(self):
        return self.capacity

    def get_current_level(self):
        return self.current_level


class Auto:
    def __init__(self, engine, fuel_tank):
        self.engine = engine
        self.fuel_tank = fuel_tank

    def get_engine(self):
        return self.engine

    def get_fuel_tank(self):
        return self.fuel_tank

    def fill_up(self, amount_fuel):
        if amount_fuel <= 0:
            print("Fuel amount cannot be zero or negative")
            return
        self.fuel_tank.fill_up(amount_fuel)

    def turn_on_engine(self):
        if self.fuel_tank.get_current_level() > 0:
            self.engine.turn_on()
        else:
            print("Cannot turn on the engine. Fuel is empty.")

    def turn_off_engine(self):
        self.engine.turn_off()

    def info(self):
        engine_state = "ON" if self.engine.get_running_state() else "OFF"
        fuel_percentage = self.fuel_tank.get_current_level()
        print(f"Engine: {engine_state}, Fuel Level: {fuel_percentage} liters")



engine = Engine()

fuel_tank = FuelTank(50)
car = Auto(engine, fuel_tank)
print("\nFilling up 20 liters of fuel:")
car.fill_up(20)  
print("\nTrying to turn on the engine:")
car.turn_on_engine() 
print("\nCar info after turning on the engine:")
car.info()  
print("\nTurning off the engine:")
car.turn_off_engine() 
print("\nCar info after turning off the engine:")
car.info()  
