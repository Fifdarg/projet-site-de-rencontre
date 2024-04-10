import math

def get_distance_between_users(lat1, lon1, lat2, lon2):
    earth_radius = 6371  # en kilomètres

    dlat = math.radians(lat2 - lat1)
    dlon = math.radians(lon2 - lon1)

    a = math.sin(dlat / 2) * math.sin(dlat / 2) + math.cos(math.radians(lat1)) * math.cos(math.radians(lat2)) * math.sin(dlon / 2) * math.sin(dlon / 2)
    c = 2 * math.asin(math.sqrt(a))
    distance = earth_radius * c

    return distance

def can_users_meet(user1, user2, max_distance):
    distance = get_distance_between_users(user1['lat'], user1['lon'], user2['lat'], user2['lon'])

    return distance <= max_distance

def filter_users_by_max_distance(users, max_distance):
    filtered_users = []

    for user in users:
        can_meet = False

        for filtered_user in filtered_users:
            if can_users_meet(user, filtered_user, max_distance):
                can_meet = True
                break

        if not can_meet:
            filtered_users.append(user)

    return filtered_users

users = [
    {'id': 1, 'lat': 48.8566, 'lon': 2.3522},
    {'id': 2, 'lat': 51.5074, 'lon': -0.1278},
    {'id': 3, 'lat': 40.7128, 'lon': -74.0060},
    # Ajoutez plus d'utilisateurs ici
]

max_distance = 1000  # en kilomètres
filtered_users = filter_users_by_max_distance(users, max_distance)

print("Liste des utilisateurs filtrés : ")
print(filtered_users)
