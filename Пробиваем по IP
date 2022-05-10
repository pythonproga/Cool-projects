import requests
from pyfiglet import Figlet
import folium


def get_info_by_ip(ip="127.0.0.1"):
    try:
        response = requests.get(url=f"http://ip-api.com/json/{ip}").json()

        data = {
            "[IP]": response.get("query"),
            "[Int prov]": response.get("isp"),
            "[Org]": response.get("org"),
            "[Country]": response.get("country"),
            "[Region Name]": response.get("regionName"),
            "[City]": response.get("city"),
            "[ZIP]": response.get("zip"),
            "[Lat]": response.get("lat"),
            "[Lon]": response.get("lon"),
            "[Status]": response.get("status"),
            "[Timezone]": response.get("timezone"),
            "[AS]": response.get("as"),
        }

        for k, v in data.items():
            print(f" {k} : {v}")

            area = folium.Map(location=[response.get("lat"), response.get("lon")], tiles="Stamen Terrain")
            tooltip = "Click me!"

            folium.Marker(
                [response.get("lat"), response.get("lon")], popup="<i>Mt. Hood Meadows</i>", tooltip=tooltip
            ).add_to(area)

            area.save(f"{response.get('query')}_{response.get('city')}.html")
    except requests.exceptions.ConnectionError:
        print("[!] Please check your connection!")


def main():
    preview_text = Figlet(font="slant")
    print(preview_text.renderText("INFO BY IP"))
    ip = input("Please enter a target IP: ")

    get_info_by_ip(ip=ip)


if __name__ == "__main__":
    main()
