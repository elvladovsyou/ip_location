import requests

def get_ip_info(ip):
    url = f"http://ip-api.com/json/{ip}?fields=status,country,regionName,city,lat,lon,timezone,isp,query"
    response = requests.get(url)
    data = response.json()
    
    if data["status"] == "fail":
        print("Ошибка: Неверный IP или запрос заблокирован.")
        return

    print(f"IP: {data['query']}")
    print(f"Страна: {data['country']}")
    print(f"Регион: {data['regionName']}")
    print(f"Город: {data['city']}")
    print(f"Координаты: {data['lat']}, {data['lon']}")
    print(f"Часовой пояс: {data['timezone']}")
    print(f"Интернет-провайдер: {data['isp']}")

ip = input("Введите IP-адрес: ")
get_ip_info(ip)
