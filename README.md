class SmartParkingSystem:
    def __init__(self, total_spots):
        self.total_spots = total_spots
        self.parking_lot = [None] * total_spots  # Initialize parking lot with empty spots

    def park_car(self, car_number):
        try:
            spot_index = self.parking_lot.index(None)  # Find the first available spot
            self.parking_lot[spot_index] = car_number
            print(f"Car {car_number} parked at spot {spot_index + 1}.")
        except ValueError:
            print("No available spots. Parking lot is full.")

    def retrieve_car(self, car_number):
        try:
            spot_index = self.parking_lot.index(car_number)  # Find the car's spot
            self.parking_lot[spot_index] = None
            print(f"Car {car_number} retrieved from spot {spot_index + 1}.")
        except ValueError:
            print(f"Car {car_number} not found in the parking lot.")

    def display_parking_lot(self):
        print("\nParking Lot Status:")
        for i, car in enumerate(self.parking_lot):
            status = f"Occupied by {car}" if car else "Available"
            print(f"Spot {i + 1}: {status}")

# Initialize the parking system with 5 spots
parking_system = SmartParkingSystem(total_spots=5)

# Menu-driven system
while True:
    print("\n=== Smart Parking System ===")
    print("1. Park a car")
    print("2. Retrieve a car")
    print("3. Display parking lot status")
    print("4. Exit")
    
    choice = input("Enter your choice (1-4): ")
    if choice == "1":
        car_number = input("Enter the car number: ")
        parking_system.park_car(car_number)
    elif choice == "2":
        car_number = input("Enter the car number to retrieve: ")
        parking_system.retrieve_car(car_number)
    elif choice == "3":
        parking_system.display_parking_lot()
    elif choice == "4":
        print("Exiting the system. Goodbye!")
        break
    else:
        print("Invalid choice. Please try again.")
        
