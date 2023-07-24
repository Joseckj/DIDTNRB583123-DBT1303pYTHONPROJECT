# DIDTNRB583123-DBT1303pYTHONPROJECT
class CarParkManager:
    def __init__(self):
        self.car_parks = {}

    def add_car_park_site(self, site_name, capacity):
        self.car_parks[site_name] = capacity

    def check_availability(self, site_name):
        return self.car_parks.get(site_name, "Site not found")

    def park_vehicle(self, site_name):
        if site_name not in self.car_parks:
            return "Site not found"

        if self.car_parks[site_name] > 0:
            self.car_parks[site_name] -= 1
            return "Vehicle parked successfully."
        else:
            return "Parking is full."

    def remove_vehicle(self, site_name):
        if site_name not in self.car_parks:
            return "Site not found"

        if self.car_parks[site_name] < self.get_capacity(site_name):
            self.car_parks[site_name] += 1
            return "Vehicle removed from the parking."
        else:
            return "No vehicles to remove."

    def get_capacity(self, site_name):
        return self.car_parks.get(site_name, "Site not found")


def main():
    car_park_manager = CarParkManager()

    while True:
        print("\nCar Park Management System")
        print("1. Add Car Park Site")
        print("2. Check Availability")
        print("3. Park Vehicle")
        print("4. Remove Vehicle")
        print("5. Exit")

        choice = input("Enter your choice (1-5): ")

        if choice == "1":
            site_name = input("Enter the site name: ")
            capacity = int(input("Enter the capacity: "))
            car_park_manager.add_car_park_site(site_name, capacity)
            print(f"{site_name} added to the car park list.")

        else if choice == "2":
            site_name = input("Enter the site name: ")
            availability = car_park_manager.check_availability(site_name)
            print(f"{site_name} has {availability} parking spots.")

        else if choice == "3":
            site_name = input("Enter the site name: ")
            result = car_park_manager.park_vehicle(site_name)
            print(result)

        else if choice == "4":
            site_name = input("Enter the site name: ")
            result = car_park_manager.remove_vehicle(site_name)
            print(result)

        else if choice == "5":
            print("Exiting Car Park Management System.")
            break

        else:
            print("Invalid choice. Please try again.")


if __name__ == "__main__":
    main()
