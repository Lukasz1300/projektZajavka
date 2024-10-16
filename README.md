# projektZajavka
Opis (streszczenie) projektu. Aplikacja do zamawiania jedzenia. 
Projekt został zrealizowany z użyciem Mavena, wraz z odpowiednimi komentarzami w pliku pom.xml:

Klasy encji w projekcie.
1. Użytkownicy i Rola
• User
− Reprezentuje użytkownika systemu, zawiera informacje o nazwie, haśle, emailu oraz danych kontaktowych.
− Posiada relacje z zamówieniami (Order) i rolami użytkownika (UserRole).
• UserRole
− Przechowuje informacje o rolach przypisanych do użytkowników.
− Posiada relację z encją Role.
• Role
− Definiuje role dostępne w systemie, takie jak ADMIN czy USER.
− Posiada relację z encją UserRole.
2. Restauracje
• Restaurant
− Reprezentuje restaurację, zawiera dane takie jak nazwa, adres, numer telefonu i email.
− Posiada relację z właścicielem restauracji (RestaurantOwner) oraz pozycjami menu (MenuItem).
• RestaurantOwner
− Reprezentuje właściciela restauracji, zawiera dane kontaktowe.
− Posiada relację z encją Restaurant.
3. Menu i Kategorie
• MenuItem
− Reprezentuje pozycję menu w restauracji, zawiera dane takie jak nazwa, opis, cena i URL do obrazu.
− Posiada relacje z kategoriami (Category) oraz pozycjami zamówień (OrderItem).
• Category
− Reprezentuje kategorię pozycje menu, na przykład "Napoje" lub "Dania główne".
− Posiada relację z pozycjami menu (MenuItem).
4. Zamówienia
• Order
− Reprezentuje zamówienie złożone przez użytkownika, zawiera informacje o statusie, łącznej cenie i adresie dostawy.
− Posiada relacje z użytkownikiem (User), restauracją (Restaurant) oraz pozycjami zamówień (OrderItem).
• OrderItem
− Reprezentuje pojedynczą pozycję w zamówieniu, zawiera informacje o ilości i cenie.
− Posiada relacje z zamówieniem (Order) oraz pozycją menu (MenuItem).
5. Obszary dostawy
• DeliveryArea
− Reprezentuje obszar dostawy, zawiera informacje o ulicy i restauracji, do której należy.
− Posiada relację z encją Restaurant.
W projekcie, są walidacje do zapewnienia, że dane wprowadzane do encji są poprawne i spełniają określone zasady. Oto podsumowanie walidacji, które występują w każdej z encji w twoim projekcie:
1. Encja Category
• Nazwa (name):
− @NotBlank: Nazwa nie może być pusta ani składać się tylko z białych znaków.
− @Size(max = 50): Maksymalna długość nazwy to 50 znaków.
2. Encja DeliveryArea
• Restauracja (restaurant):
− @NotNull: Restauracja nie może być pusta.
• Nazwa ulicy (streetName):
− @NotBlank: Nazwa ulicy jest wymagana.
− @Size(max = 255): Maksymalna długość to 255 znaków.
3. Encja MenuItem
• Restauracja (restaurant):
− @NotNull: Restauracja nie może być pusta.
• Nazwa pozycji menu (name):
− @NotBlank: Nazwa pozycji menu jest wymagana.
− @Size(max = 100): Maksymalna długość to 100 znaków.
• Opis (description):
− @Size(max = 2000): Maksymalna długość opisu to 2000 znaków.
• Cena (price):
− @NotNull: Cena jest wymagana.
− @Positive: Cena musi być większa niż zero.
• Adres URL obrazu (imageUrl):
− @Size(max = 255): Maksymalna długość to 255 znaków.
4. Encja Order
• Użytkownik (user):
− @NotNull: Użytkownik nie może być pusty.
• Restauracja (restaurant):
− @NotNull: Restauracja nie może być pusta.
• Status zamówienia (orderStatus):
− @NotBlank: Status zamówienia nie może być pusty.
− @Size(max = 50): Maksymalna długość to 50 znaków.
• Całkowita cena (totalPrice):
− @NotNull: Całkowita cena nie może być pusta.
− @Positive: Całkowita cena musi być dodatnia.
• Data zamówienia (orderDate):
− @NotNull: Data zamówienia nie może być pusta.
− @PastOrPresent: Data zamówienia nie może być w przyszłości.
• Adres dostawy (deliveryAddress):
− @NotBlank: Adres dostawy nie może być pusty.
− @Size(max = 255): Maksymalna długość to 255 znaków.
5. Encja OrderItem
• Zamówienie (order):
− @NotNull: Zamówienie nie może być puste.
• Pozycja menu (menuItem):
− @NotNull: Pozycja menu nie może być pusta.
• Ilość (quantity):
− @NotNull: Ilość nie może być pusta.
− @Positive: Ilość musi być dodatnia.
• Cena (price):
− @NotNull: Cena nie może być pusta.
− @Positive: Cena musi być dodatnia.
6. Encja Restaurant
• Nazwa (name):
− @NotBlank: Nazwa jest wymagana.
− @Size(max = 100): Maksymalna długość to 100 znaków.
• Adres (address):
− @NotBlank: Adres jest wymagany.
− @Size(max = 255): Maksymalna długość to 255 znaków.
• Numer telefonu (phoneNumber):
− @Pattern: Numer telefonu musi spełniać określony wzór.
• Email (email):
− @Email: Email powinien być prawidłowy.
− @Size(max = 100): Maksymalna długość to 100 znaków.
7. Encja RestaurantOwner
• Nazwa właściciela (name):
− @NotBlank: Nazwa właściciela jest wymagana.
− @Size(max = 100): Maksymalna długość to 100 znaków.
• Email (email):
− @NotBlank: Email jest wymagany.
− @Email: Email powinien być prawidłowy.
− @Size(max = 100): Maksymalna długość to 100 znaków.
• Numer telefonu (phoneNumber):
− @Pattern: Numer telefonu musi spełniać określony wzór.
8. Encja Role
• Nazwa roli (name):
− @NotBlank: Nazwa nie może być pusta.
− @Size(max = 50): Maksymalna długość to 50 znaków.
9. Encja User
• Nazwa użytkownika (username):
− @NotBlank: Nazwa użytkownika jest wymagana.
− @Size(max = 50): Maksymalna długość to 50 znaków.
• Hasło (password):
− @NotBlank: Hasło jest wymagane.
− @Size(min = 6, max = 100): Długość hasła od 6 do 100 znaków.
• Email (email):
− @NotBlank: Email jest wymagany.
− @Email: Email powinien być prawidłowy.
− @Size(max = 100): Maksymalna długość to 100 znaków.
• Imię (firstName):
− @Size(max = 50): Maksymalna długość to 50 znaków.
• Nazwisko (lastName):
− @Size(max = 50): Maksymalna długość to 50 znaków.
• Numer telefonu (phoneNumber):
− @Pattern: Numer telefonu musi spełniać określony wzór.
• Adres (address):
− @Size(max = 255): Maksymalna długość to 255 znaków.
Podsumowanie
Każda encja w projekcie ma przypisane reguły walidacji, które pomagają zapewnić integralność danych. Użycie adnotacji takich jak @NotBlank, @NotNull, @Positive i inne umożliwia łatwe sprawdzanie poprawności danych przed ich zapisaniem w bazie danych. Te walidacje są kluczowe dla stabilności i bezpieczeństwa aplikacji.
Oto szczegółowy opis relacji pomiędzy encjami w projekcie:
1. Category
• Relacja: Wiele-do-wielu z MenuItem.
• Opis: Kategoria może zawierać wiele pozycji w menu, a pozycja w menu może należeć do wielu kategorii. Relacja ta jest realizowana przez tabelę pośredniczącą menu_item_categories.
2. DeliveryArea
• Relacja: Wiele-do-jednego z Restaurant.
• Opis: Obszar dostawy jest powiązany z jedną restauracją, ale jedna restauracja może mieć wiele obszarów dostawy.
3. MenuItem
• Relacje:
− Wiele-do-jednego z Restaurant.
− Wiele-do-wielu z Category.
− Wiele-do-jednego z OrderItem.
• Opis:
− Pozycja menu należy do jednej restauracji, ale restauracja może oferować wiele pozycji menu.
− Pozycja menu może należeć do wielu kategorii, a kategoria może mieć wiele pozycji menu.
− Każda pozycja menu może być częścią wielu zamówień (przez OrderItem).
4. Order
• Relacje:
− Wiele-do-jednego z User.
− Wiele-do-jednego z Restaurant.
− Wiele-do-wielu z OrderItem.
• Opis:
− Zamówienie jest powiązane z jednym użytkownikiem i jedną restauracją, ale każdy użytkownik może mieć wiele zamówień.
− Zamówienie może składać się z wielu pozycji zamówienia (OrderItem), a pozycja zamówienia jest związana z jednym zamówieniem.
5. OrderItem
• Relacje:
− Wiele-do-jednego z Order.
− Wiele-do-jednego z MenuItem.
• Opis:
− Pozycja zamówienia jest powiązana z jednym zamówieniem i jedną pozycją w menu. Każda pozycja zamówienia dotyczy konkretnej pozycji w menu i jest częścią jednego zamówienia.
6. Restaurant
• Relacje:
− Wiele-do-jednego z RestaurantOwner.
− Wiele-do-wielu z MenuItem.
• Opis:
− Restauracja może mieć jednego właściciela (restauratora), ale jeden właściciel może posiadać wiele restauracji.
− Restauracja oferuje wiele pozycji w menu, a pozycja w menu należy do jednej restauracji.
7. RestaurantOwner
• Relacje:
− Wiele-do-jednego z Restaurant.
• Opis:
− Właściciel restauracji może mieć wiele restauracji, ale każda restauracja jest przypisana do jednego właściciela.
8. Role
• Relacje:
− Wiele-do-wielu z UserRole.
• Opis:
− Rola może być przypisana do wielu użytkowników poprzez encję UserRole, a jeden użytkownik może mieć wiele ról.
9. User
• Relacje:
− Wiele-do-wielu z UserRole.
− Wiele-do-jednego z Order.
• Opis:
− Użytkownik może mieć wiele ról, a każda rola jest reprezentowana przez UserRole.
− Użytkownik może mieć wiele zamówień.
10. UserRole
• Relacje:
− Wiele-do-jednego z User.
− Wiele-do-jednego z Role.
• Opis:
− Użytkownik roli jest pośrednikiem pomiędzy użytkownikami a rolami, umożliwiając przypisanie wielu ról do jednego użytkownika i vice versa

src/main/resources/db.migration/V1__create_tables.sql
Struktura bazy danych składa się z kilku tabel, które współpracują ze sobą, aby obsługiwać funkcjonalności aplikacji związanej z restauracjami i zamówieniami. Oto krótki opis każdej z tabel oraz ich kluczowych elementów:
Opis tabel:
1. Tabela users
− Przechowuje dane użytkowników aplikacji.
− Pola: id, username, password, email, first_name, last_name, phone_number, address, created_at.
− Używa unikalnych ograniczeń na username i email, a także walidacji dla email i phone_number.
2. Tabela restaurant_owners
− Rejestruje właścicieli restauracji.
− Pola: id, user_id.
− user_id jest kluczem obcym odnoszącym się do tabeli users.
3. Tabela restaurants
− Przechowuje informacje o restauracjach.
− Pola: id, owner_id, name, address, phone_number, email, description, created_at.
− owner_id odnosi się do tabeli restaurant_owners, co pozwala powiązać restaurację z jej właścicielem.
4. Tabela menu_items
− Zawiera pozycje menu dla restauracji.
− Pola: id, restaurant_id, name, description, price, image_url, created_at.
− restaurant_id jest kluczem obcym odnoszącym się do tabeli restaurants.
5. Tabela orders
− Rejestruje zamówienia składane przez użytkowników.
− Pola: id, user_id, restaurant_id, order_status, total_price, order_date, delivery_address.
− user_id oraz restaurant_id są kluczami obcymi odnoszącymi się do tabel users i restaurants.
6. Tabela order_items
− Zawiera szczegóły zamówień, takie jak pozycje menu i ich ilości.
− Pola: id, order_id, menu_item_id, quantity, price.
− order_id oraz menu_item_id są kluczami obcymi odnoszącymi się do tabel orders i menu_items.
7. Tabela categories
− Przechowuje kategorie dla pozycji menu.
− Pole: id, name, z unikalnym ograniczeniem na name.
8. Tabela menu_item_categories
− Umożliwia powiązanie pozycji menu z kategoriami.
− Pola: menu_item_id, category_id.
− Pola te tworzą klucz główny z kombinacji menu_item_id i category_id, a także są kluczami obcymi.
9. Tabela delivery_areas
− Przechowuje obszary dostawy dla restauracji.
− Pola: id, restaurant_id, street_name.
− restaurant_id jest kluczem obcym odnoszącym się do tabeli restaurants.
10. Tabela roles
− Zawiera role, które mogą być przypisane do użytkowników.
− Pole: id, name, z unikalnym ograniczeniem na name.
11. Tabela user_roles
− Umożliwia powiązanie użytkowników z rolami.
− Pola: user_id, role_id.
− Te pola tworzą klucz główny z kombinacji user_id i role_id, a także są kluczami obcymi.
Podsumowanie:
Ta struktura bazy danych umożliwia kompleksowe zarządzanie użytkownikami, właścicielami restauracji, restauracjami, zamówieniami, pozycjami menu, kategoriami, obszarami dostawy i rolami w aplikacji. Każda tabela ma zdefiniowane odpowiednie relacje, co umożliwia efektywne zarządzanie danymi oraz ich integralność.

src/main/resources/db.migration/V2__insert_initial_data.sql
Opis zapytań SQL:

1. Dodawanie podstawowych ról:
INSERT INTO roles (name) VALUES ('ROLE_USER');
INSERT INTO roles (name) VALUES ('ROLE_ADMIN');
Wstawia dwie podstawowe role do tabeli roles: ROLE_USER oraz ROLE_ADMIN.

2. Wstawienie przykładowych użytkowników:
INSERT INTO users (username, password, email, first_name, last_name, phone_number, address)
VALUES
('john_doe', 'password123', 'john.doe@example.com', 'John', 'Doe', '1234567890', 'ul. Piękna 12, Warszawa'),
('jane_smith', 'password321', 'jane.smith@example.com', 'Jane', 'Smith', '1287654321', 'ul. Lechitów 45, Kraków');
Dodaje dwóch użytkowników: john_doe oraz jane_smith, wraz z ich danymi kontaktowymi.

3. Wstawienie właścicieli lokali gastronomicznych:
INSERT INTO restaurant_owners (user_id)
VALUES
((SELECT id FROM users WHERE username = 'john_doe'));
Rejestruje john_doe jako właściciela lokalu gastronomicznego w tabeli restaurant_owners.

4. Wstawienie restauracji:
INSERT INTO restaurants (owner_id, name, address, phone_number, email, description)
VALUES
((SELECT id FROM restaurant_owners WHERE user_id = (SELECT id FROM users WHERE username = 'john_doe')), 'Pizzeria Bella', 'ul. Kwiatowa 10, Warszawa', '22-123-456', 'kontakt@pizzeriabella.pl', 'Pyszna pizza na cienkim cieście.'),
((SELECT id FROM restaurant_owners WHERE user_id = (SELECT id FROM users WHERE username = 'john_doe')), 'Sushi Mistrz', 'ul. Leśna 5, Kraków', '12-345-678', 'info@sushimistrz.pl', 'Autentyczne sushi przygotowywane przez mistrza kuchni.');
Wstawia dwie restauracje, Pizzeria Bella i Sushi Mistrz, przypisując john_doe jako ich właściciela.

5. Wstawienie pozycji menu:
INSERT INTO menu_items (restaurant_id, name, description, price, image_url)
VALUES
((SELECT id FROM restaurants WHERE name = 'Pizzeria Bella'), 'Pizza Margherita', 'Klasyczna pizza z sosem pomidorowym i bazylią.', 29.99, 'http://example.com/images/pizza_margherita.jpg'),
((SELECT id FROM restaurants WHERE name = 'Pizzeria Bella'), 'Pizza Pepperoni', 'Ostra pizza z pepperoni i serem mozzarella.', 34.99, 'http://example.com/images/pizza_pepperoni.jpg'),
((SELECT id FROM restaurants WHERE name = 'Sushi Mistrz'), 'Sushi California', 'Świeży krab i awokado zawinięte w wodorosty.', 24.99, 'http://example.com/images/sushi_california.jpg'),
((SELECT id FROM restaurants WHERE name = 'Sushi Mistrz'), 'Sushi Spicy Tuna', 'Ostry tuńczyk z ogórkiem i awokado.', 29.99, 'http://example.com/images/sushi_spicy_tuna.jpg');
Dodaje pozycje menu dla obu restauracji.

6. Wstawienie kategorii menu:
INSERT INTO categories (name)
VALUES
('Przystawki'),
('Dania główne'),
('Desery'),
('Napoje');

7. Powiązanie pozycji menu z kategoriami:
INSERT INTO menu_item_categories (menu_item_id, category_id)
VALUES
((SELECT id FROM menu_items WHERE name = 'Pizza Margherita'), (SELECT id FROM categories WHERE name = 'Dania główne')),
((SELECT id FROM menu_items WHERE name = 'Pizza Pepperoni'), (SELECT id FROM categories WHERE name = 'Dania główne')),
((SELECT id FROM menu_items WHERE name = 'Sushi California'), (SELECT id FROM categories WHERE name = 'Dania główne')),
((SELECT id FROM menu_items WHERE name = 'Sushi Spicy Tuna'), (SELECT id FROM categories WHERE name = 'Dania główne'));
Umożliwia powiązanie pozycji menu z odpowiednimi kategoriami.

8. Wstawienie obszarów dostawy:
INSERT INTO delivery_areas (restaurant_id, street_name)
VALUES
((SELECT id FROM restaurants WHERE name = 'Pizzeria Bella'), 'ul. Ogrodowa 10, Warszawa'),
((SELECT id FROM restaurants WHERE name = 'Pizzeria Bella'), 'ul. Leśna 5, Warszawa'),
((SELECT id FROM restaurants WHERE name = 'Sushi Mistrz'), 'ul. Żółwia 3, Kraków'),
((SELECT id FROM restaurants WHERE name = 'Sushi Mistrz'), 'ul. Polan 7, Kraków');
Dodaje obszary dostawy dla obu restauracji.

9. Przypisanie ról do użytkowników:
INSERT INTO user_roles (user_id, role_id)
VALUES
((SELECT id FROM users WHERE username = 'john_doe'), (SELECT id FROM roles WHERE name = 'ROLE_ADMIN')),
((SELECT id FROM users WHERE username = 'jane_smith'), (SELECT id FROM roles WHERE name = 'ROLE_USER'));
Przypisuje role do użytkowników: john_doe jako administratora oraz jane_smith jako użytkownika.

W powyższych przykładach mamy dwa pliki migracyjne (V1__create_tables.sql i V2__insert_initial_data.sql), które są używane do zarządzania schematem bazy danych oraz danymi początkowymi w projekcie przy użyciu narzędzia Flyway.

V1__create_tables.sql — zawiera definicje tabel w bazie danych.
V2__insert_initial_data.sql — zawiera wstawienie danych początkowych.

Format nazw plików migracyjnych
Pliki migracyjne w Flyway muszą być zgodne z określoną konwencją nazewnictwa:

sql V{nr_wersji}__{opis}.sql
    V — oznacza wersję.
    nr_wersji — numer wersji, który określa kolejność migracji.
    opis — dowolny opis, który ma pomóc w zrozumieniu, czego dotyczy migracja (np. create_tables).

Dzięki tej migracji, gdy aplikacja jest uruchamiana po raz pierwszy, baza danych zostaje wypełniona przykładowymi danymi, co ułatwia testowanie funkcjonalności aplikacji.
Po dodaniu zależności, Flyway automatycznie zacznie szukać migracji w katalogu src/main/resources/db/migration podczas uruchamiania aplikacji.

Podsumowanie:
W powyższym projekcie Flyway zarządza schematem bazy danych i początkowymi danymi, co pozwala łatwo wdrażać zmiany w strukturze bazy oraz wprowadzać dane testowe. Każdy kolejny plik migracyjny (np. V3__add_reviews_table.sql) można tworzyć w podobny sposób, zwiększając numer wersji i dodając odpowiednie zmiany w bazie danych.

Opis repozytoriów na podstawie implementacji:
1. CategoryRepository
• Opis: Repozytorium do obsługi encji Category. Dziedziczy z JpaRepository, co umożliwia podstawowe operacje CRUD.
2. DeliveryAreaRepository
• Opis: Repozytorium do obsługi encji DeliveryArea. Oprócz operacji CRUD, zawiera metodę findByRestaurantId, która umożliwia wyszukiwanie obszarów dostawy na podstawie identyfikatora restauracji.
3. MenuItemRepository
Opis: Repozytorium do obsługi encji MenuItem. Zawiera metodę findByRestaurantId, która pozwala na wyszukiwanie pozycji menu według identyfikatora restauracji.
4. OrderItemRepository
• Opis: Repozytorium do obsługi encji OrderItem. Oferuje metody findByOrderId i findByMenuItemId, które umożliwiają wyszukiwanie pozycji zamówienia na podstawie identyfikatorów zamówienia i pozycji menu.
5. OrderRepository
• Opis: Repozytorium do obsługi encji Order. Zawiera metody findByUserId i findByRestaurantId, które umożliwiają wyszukiwanie zamówień według identyfikatora użytkownika oraz identyfikatora restauracji.
6. RestaurantOwnerRepository
• Opis: Repozytorium do obsługi encji RestaurantOwner. Dziedziczy z JpaRepository, co zapewnia dostęp do podstawowych operacji CRUD.
7. RestaurantRepository
• Opis: Repozytorium do obsługi encji Restaurant. Zawiera metodę findByOwnerId, która pozwala na wyszukiwanie restauracji na podstawie identyfikatora właściciela.
8. UserRepository
• Opis: Repozytorium do obsługi encji User. Oferuje metody do sprawdzania istnienia użytkownika po nazwie użytkownika (existsByUsername), a także do wyszukiwania użytkowników według nazwy użytkownika i adresu e-mail.
Podsumowanie
Wszystkie repozytoria korzystają z interfejsu JpaRepository, co umożliwia efektywne zarządzanie encjami i podstawowe operacje na bazie danych. Dodatkowo, każde repozytorium zawiera niestandardowe metody do wyszukiwania danych zgodnie z wymaganiami projektu.
Oto skrócony opis serwisów na podstawie implementacji:
1. CategoryService
• Opis: Serwis do obsługi encji Category. Umożliwia pobieranie wszystkich kategorii, zapisywanie nowej kategorii, usuwanie kategorii po identyfikatorze oraz wyszukiwanie kategorii po identyfikatorze.
2. CurrencyService
• Opis: Serwis odpowiedzialny za pobieranie kursu dolara amerykańskiego z zewnętrznego API. Używa RestTemplate do komunikacji z API oraz ObjectMapper do analizy odpowiedzi JSON.
3. CustomUserDetailsService
• Opis: Serwis implementujący interfejs UserDetailsService. Odpowiada za ładowanie użytkowników na podstawie nazwy użytkownika, korzystając z repozytorium UserRepository.
4. DeliveryAreaService
• Opis: Serwis do obsługi encji DeliveryArea. Umożliwia wyszukiwanie obszarów dostawy na podstawie identyfikatora restauracji.
5. MenuItemService
• Opis: Serwis do obsługi encji MenuItem. Umożliwia pobieranie wszystkich pozycji menu, wyszukiwanie pozycji po identyfikatorze, wyszukiwanie pozycji menu na podstawie identyfikatora restauracji oraz zapisywanie i usuwanie pozycji menu.
6. OrderItemService
• Opis: Serwis do obsługi encji OrderItem. Umożliwia pobieranie wszystkich pozycji zamówienia, wyszukiwanie pozycji zamówienia po identyfikatorze oraz według identyfikatorów zamówienia i pozycji menu.
7. OrderService
• Opis: Serwis do obsługi encji Order. Umożliwia pobieranie wszystkich zamówień, wyszukiwanie zamówienia po identyfikatorze, a także według identyfikatorów użytkownika i restauracji.
8. RestaurantOwnerService
• Opis: Serwis do obsługi encji RestaurantOwner. Umożliwia wyszukiwanie właściciela restauracji po identyfikatorze. Istnieje możliwość dodania metod do aktualizacji właściciela.
9. RestaurantService
• Opis: Serwis do obsługi encji Restaurant. Umożliwia pobieranie wszystkich restauracji, wyszukiwanie restauracji po identyfikatorze oraz według identyfikatora właściciela.
10. UserService
• Opis: Serwis do obsługi encji User. Umożliwia pobieranie wszystkich użytkowników, wyszukiwanie użytkownika po identyfikatorze, nazwie użytkownika i adresie e-mail, a także zapisywanie i usuwanie użytkowników.
Podsumowanie
Każdy serwis w projekcie pełni określoną funkcję i zapewnia dostęp do odpowiednich repozytoriów, umożliwiając realizację operacji na encjach. Serwisy są oznaczone adnotacją @Service, a większość z nich korzysta z transakcji, co zapewnia bezpieczeństwo operacji bazodanowych.
Oto kilka dodatkowych informacji, które mogą być wartościowe w kontekście serwisów w projekcie:
1. Zasady SOLID
• Zastosowanie zasad SOLID (zwłaszcza zasady pojedynczej odpowiedzialności) w projektowaniu serwisów. Każdy serwis odpowiada za konkretną encję i jej logikę biznesową, co ułatwia zarządzanie kodem oraz jego testowanie.
2. Obsługa błędów
• Warto dodać mechanizmy obsługi błędów, które mogą wystąpić podczas operacji bazodanowych, takie jak EntityNotFoundException w RestaurantOwnerService, aby informować użytkowników o niepoprawnych operacjach.
3. Walidacja danych
• Implementacja walidacji danych przy zapisywaniu encji (np. saveCategory, saveMenuItem, itp.), co pozwala na zapewnienie, że do bazy danych trafiają tylko poprawne dane.
4. Cache'owanie
• Możliwość implementacji cache'owania, aby poprawić wydajność odczytów danych, zwłaszcza w przypadku często wywoływanych metod, takich jak findAll.
5. Logowanie
• Użycie loggera (np. Slf4j) do logowania operacji, co może pomóc w debugowaniu oraz monitorowaniu działań aplikacji. Możesz logować istotne informacje, takie jak wprowadzenie danych, czas wykonania operacji, czy wystąpienie błędów.
6. Adnotacje transakcyjne
• Użycie adnotacji @Transactional w odpowiednich metodach, aby zapewnić, że operacje związane z bazą danych są wykonywane w kontekście transakcji.

Opisy kontrolerów:
1. CategoryController
− Opis: Odpowiedzialny za zarządzanie kategoriami w aplikacji.
− Endpointy:
• GET /categories - Pobranie wszystkich kategorii.
• GET /categories/new - Wyświetlenie formularza do tworzenia nowej kategorii.
• POST /categories - Zapisanie nowej kategorii.
• DELETE /categories/delete/{id} - Usunięcie kategorii po identyfikatorze.
2. CurrencyController
− Opis: Obsługuje żądania związane z kursami walutowymi.
− Endpointy:
• GET /api/usd-rate - Pobranie aktualnego kursu USD.
3. CustomErrorController
− Opis: Umożliwia obsługę błędów w aplikacji.
− Endpointy:
• GET /templates/error - Zwraca widok błędu 404.
4. DeliveryAreaController
− Opis: Odpowiedzialny za zarządzanie obszarami dostawy.
− Endpointy:
• GET /deliveryareas/restaurant/{restaurantId} - Pobranie wszystkich obszarów dostawy dla danej restauracji.
5. MenuItemController
− Opis: Zarządza pozycjami menu w aplikacji.
− Endpointy:
• GET /menu-item - Pobranie wszystkich pozycji menu.
• GET /menu-item/restaurant/{restaurantId} - Pobranie pozycji menu według identyfikatora restauracji.
• GET /menu-item/{id} - Pobranie pozycji menu po identyfikatorze.
• GET /menu-item/new - Wyświetlenie formularza do dodania nowej pozycji menu.
• POST /menu-item - Zapisanie nowej pozycji menu.
• DELETE /menu-item/delete/{id} - Usunięcie pozycji menu po identyfikatorze.
6. OrderController
− Opis: Odpowiedzialny za zarządzanie zamówieniami w aplikacji.
− Endpointy:
• GET /orders - Pobranie wszystkich zamówień.
• GET /orders/{id} - Pobranie zamówienia po identyfikatorze.
• GET /orders/user/{userId} - Pobranie zamówień użytkownika po jego identyfikatorze.
• GET /orders/restaurant/{restaurantId} - Pobranie zamówień restauracji po jej identyfikatorze.
• GET /orders/new - Wyświetlenie formularza do tworzenia nowego zamówienia.
• POST /orders - Zapisanie nowego zamówienia.
• DELETE /orders/delete/{id} - Usunięcie zamówienia po identyfikatorze.
7. OrderItemController
− Opis: Zarządza pozycjami zamówień w aplikacji.
− Endpointy:
• GET /order-items - Pobranie wszystkich pozycji zamówień.
• GET /order-items/new - Wyświetlenie formularza do dodania nowej pozycji zamówienia.
• POST /order-items - Zapisanie nowej pozycji zamówienia.
• GET /order-items/{id} - Pobranie pozycji zamówienia po identyfikatorze.
• DELETE /order-items/delete/{id} - Usunięcie pozycji zamówienia po identyfikatorze.
8. RestaurantController
− Opis: Odpowiedzialny za zarządzanie restauracjami w aplikacji.
− Endpointy:
• GET /restaurants - Pobranie wszystkich restauracji.
• GET /restaurants/{id} - Pobranie restauracji po identyfikatorze.
• GET /restaurants/owner/{ownerId} - Pobranie restauracji według identyfikatora właściciela.
• GET /restaurants/new - Wyświetlenie formularza do dodania nowej restauracji.
• POST /restaurants - Zapisanie nowej restauracji.
• DELETE /restaurants/delete/{id} - Usunięcie restauracji po identyfikatorze.
9. RestaurantOwnerController
− Opis: Odpowiedzialny za zarządzanie właścicielami restauracji w aplikacji.
− Endpointy:
• GET /restaurant-owners/{id} - Pobranie właściciela restauracji po identyfikatorze.
10. UserController
− Opis: Zarządza użytkownikami w aplikacji.
− Endpointy:
• GET /users - Pobranie wszystkich użytkowników.
• GET /users/{id} - Pobranie użytkownika po identyfikatorze.
• GET /users/username/{username} - Pobranie użytkownika po nazwie użytkownika.
Oto krótki opis kontrolerów REST API w projekcie, który zarządza kategoriami:
1. CategoryRestController
• Endpoint: /api/categories
• Funkcje:
− GET - Pobranie wszystkich kategorii.
− POST - Dodanie nowej kategorii.
− PUT - Aktualizacja kategorii na podstawie ID.
− DELETE - Usunięcie kategorii na podstawie ID.
2. DeliveryAreaRestController
• Endpoint: /api/deliveryareas
• Funkcje:
− GET /restaurant/{restaurantId} - Pobranie wszystkich obszarów dostawy dla danej restauracji.
3. MenuItemRestController
• Endpoint: /api/menu-items
• Funkcje:
− GET - Pobranie wszystkich pozycji menu.
− GET /restaurant/{restaurantId} - Pobranie pozycji menu dla danej restauracji.
− GET /{id} - Pobranie pozycji menu według ID.
− POST - Dodanie nowej pozycji menu.
− PUT - Aktualizacja pozycji menu na podstawie ID.
− DELETE - Usunięcie pozycji menu na podstawie ID.
4. OrderItemRestController
• Endpoint: /api/order-items
• Funkcje:
− GET - Pobranie wszystkich pozycji zamówień.
− GET /{id} - Pobranie pozycji zamówienia według ID.
− GET /order/{orderId} - Pobranie pozycji zamówień według ID zamówienia.
− GET /menu-item/{menuItemId} - Pobranie pozycji zamówień według ID pozycji menu.
− POST - Dodanie nowego elementu zamówienia.
− PUT - Aktualizacja pozycji zamówienia na podstawie ID.
− DELETE - Usunięcie pozycji zamówienia na podstawie ID.
5. OrderRestController
• Endpoint: /api/orders
• Funkcje:
− GET - Pobranie wszystkich zamówień.
− GET /{id} - Pobranie zamówienia według ID.
− GET /user/{userId} - Pobranie zamówień według ID użytkownika.
− GET /restaurant/{restaurantId} - Pobranie zamówień według ID restauracji.
− POST - Dodanie nowego zamówienia.
− PUT - Aktualizacja zamówienia na podstawie ID.
− DELETE - Usunięcie zamówienia na podstawie ID.
6. RestaurantOwnerRestController
• Endpoint: /api/restaurant-owners
• Funkcje:
− GET /{id} - Pobranie właściciela restauracji według ID.
7. RestaurantRestController
• Endpoint: /api/restaurants
• Funkcje:
− GET - Pobranie wszystkich restauracji.
− GET /{id} - Pobranie restauracji według ID.
− GET /owner/{ownerId} - Pobranie restauracji według ID właściciela.
− POST - Dodanie nowej restauracji.
− PUT - Aktualizacja restauracji na podstawie ID.
− DELETE - Usunięcie restauracji według ID.
8. UserRestController
• Endpoint: /api/users
• Funkcje:
− GET - Pobranie wszystkich użytkowników (tylko dla adminów).
− GET /{id} - Pobranie użytkownika po ID.
− GET /username/{username} - Pobranie użytkownika po nazwie użytkownika.
− GET /email/{email} - Pobranie użytkownika po emailu.
− POST - Dodanie nowego użytkownika (tylko dla adminów).
− PUT /{id} - Edytowanie istniejącego użytkownika (tylko dla adminów).
− DELETE /{id} - Usuwanie użytkownika (tylko dla adminów).
Każdy z kontrolerów obsługuje odpowiednie operacje na zasobach, zapewniając możliwość zarządzania danymi w aplikacji oraz integrację z frontendem.
Do czego służy klasa NBPClient odnośnie punktu 18 oraz 19 testy Wiremock klasa: CurrencyServiceTest 
Klasa NBPClient jest używana w aplikacji do:
• Komunikacji z zewnętrznym API NBP w celu uzyskania aktualnych danych o kursie USD.
• Ułatwienia integracji z API, dzięki czemu inne komponenty aplikacji mogą łatwo pobierać kurs USD, wywołując metodę getUsdRate().
• Umożliwienia testowania i zamockowania logiki pobierania kursów walut w testach jednostkowych i integracyjnych, ponieważ klasa jest oznaczona jako komponent Spring.
Podsumowując, NBPClient jest kluczowym elementem, który umożliwia dynamiczne pobieranie informacji o kursie dolara amerykańskiego w aplikacji, co może być użyteczne w różnych kontekstach, takich jak przeliczanie cen, wyświetlanie kursów walutowych użytkownikom, czy inne operacje wymagające znajomości aktualnego kursu USD.
Klasa JacksonConfig jest klasą konfiguracyjną w aplikacji Spring, która odpowiada za konfigurację serializacji i deserializacji obiektów JSON przy użyciu biblioteki Jackson. Oto kluczowe elementy tej klasy:
Elementy klasy:
1. Adnotacja @Configuration:
− Oznacza, że klasa zawiera definicje beanów, które będą zarządzane przez kontener Springa.
2. Metoda objectMapper():
− Metoda ta jest oznaczona adnotacją @Bean, co sprawia, że zwraca obiekt ObjectMapper, który jest rejestrowany jako bean w kontekście aplikacji Spring.
− Tworzy nową instancję ObjectMapper i rejestruje moduł JavaTimeModule, co pozwala na poprawną obsługę typów dat i czasu z pakietu java.time (np. LocalDate, LocalDateTime).
Podsumowanie:
Klasa JacksonConfig konfiguruje bibliotekę Jackson w aplikacji, zapewniając, że obiekty typu java.time będą prawidłowo serializowane i deserializowane podczas pracy z danymi JSON. Umożliwia to lepszą obsługę dat i czasów w aplikacji, co jest szczególnie przydatne w przypadku operacji związanych z czasem.
Klasa RestTemplateConfig jest klasą konfiguracyjną w aplikacji Spring, która odpowiada za konfigurację klienta HTTP RestTemplate. Oto kluczowe elementy tej klasy:
Elementy klasy:
1. Adnotacja @Configuration:
− Oznacza, że klasa zawiera definicje beanów, które będą zarządzane przez kontener Springa.
2. Metoda restTemplate():
− Metoda ta jest oznaczona adnotacją @Bean, co sprawia, że zwraca obiekt RestTemplate, który jest rejestrowany jako bean w kontekście aplikacji Spring.
− Tworzy nową instancję RestTemplate, co umożliwia wykonywanie żądań HTTP w aplikacji.
Podsumowanie:
Klasa RestTemplateConfig konfiguruje i dostarcza instancję RestTemplate, co ułatwia komunikację z zewnętrznymi usługami za pomocą protokołu HTTP w aplikacji Spring. Dzięki temu komponenty aplikacji mogą łatwo korzystać z tej instancji do wysyłania zapytań i otrzymywania odpowiedzi z API.
Klasa SecurityConfig jest klasą konfiguracyjną odpowiedzialną za konfigurację bezpieczeństwa w aplikacji Spring. Używa biblioteki Spring Security do zarządzania autoryzacją i uwierzytelnianiem. Oto kluczowe elementy tej klasy:
Elementy klasy:
1. Adnotacje:
− @Configuration: Oznacza, że klasa zawiera definicje beanów, które będą zarządzane przez kontener Springa.
− @EnableWebSecurity: Włącza wsparcie dla bezpieczeństwa webowego w aplikacji.
2. Metoda passwordEncoder():
− Zwraca instancję BCryptPasswordEncoder, która jest używana do kodowania haseł. To pozwala na bezpieczne przechowywanie haseł użytkowników.
3. Metoda securityFilterChain(HttpSecurity http):
− Definiuje reguły bezpieczeństwa dla aplikacji.
− Konfiguracja CSRF: Ignoruje zabezpieczenie CSRF dla określonych endpointów (np. /h2-console/**, /security/login).
− Ustalanie uprawnień: Umożliwia dostęp do różnych endpointów w zależności od ról (np. /api/users i /api/categories/** wymagają roli ADMIN).
− Konfiguracja formularza logowania: Ustala niestandardową stronę logowania i pozwala na dostęp do niej dla wszystkich użytkowników.
− Umożliwia wylogowanie dla wszystkich użytkowników.
4. Metoda authManager(HttpSecurity http):
− Tworzy AuthenticationManager, który zarządza użytkownikami w pamięci.
− Dodaje dwóch użytkowników: testuser i admin, obydwaj z rolą ADMIN, oraz odpowiednimi hasłami, które są kodowane.
Podsumowanie:
Klasa SecurityConfig konfiguruje mechanizmy bezpieczeństwa aplikacji Spring, definiując sposób uwierzytelniania i autoryzacji użytkowników. Umożliwia dostęp do różnych zasobów w zależności od ról użytkowników, a także definiuje reguły dotyczące logowania i wylogowywania. Ponadto, obsługuje kodowanie haseł przy użyciu algorytmu BCrypt, co zwiększa bezpieczeństwo aplikacj
Klasa SwaggerConfig onosi się do punktu 16 jest odpowiedzialna za konfigurację dokumentacji API w aplikacji Spring przy użyciu Swaggera (lub OpenAPI). Umożliwia generowanie dokumentacji w formacie, który może być przeglądany w interfejsie użytkownika SwaggerUI. Oto kluczowe elementy tej klasy:
Elementy klasy:
1. Adnotacje:
− @Configuration: Oznacza, że klasa jest klasą konfiguracyjną, co pozwala Springowi na zarządzanie jej komponentami.
− @Bean: Oznacza, że metoda publicApi() zwraca obiekt, który ma być zarządzany przez kontener Springa.
2. Metoda publicApi():
− Tworzy konfigurację grupy API dla SwaggerUI.
− Używa klasy GroupedOpenApi do zdefiniowania grupy API.
− Ustala nazwę grupy na "public".
− Określa, że wszystkie endpointy pasujące do wzorca /api/** będą uwzględnione w tej grupie API.
Podsumowanie:
Klasa SwaggerConfig konfigurueuje Swaggera w aplikacji, definiując grupę API, która będzie dokumentowana. Endpointy pasujące do wzorca /api/** będą wyświetlane w SwaggerUI pod nazwą grupy "public". Dzięki tej klasie użytkownicy mogą łatwo przeglądać i testować API aplikacji w interfejsie Swaggera, co ułatwia rozwój i integrację.
Klasa ProjektZajavka2Application jest główną klasą aplikacji Spring Boot, która pełni rolę punktu wejścia. Oto krótki opis jej elementów:
Kluczowe elementy klasy:
1. Adnotacja @SpringBootApplication:
− To złożona adnotacja, która łączy trzy inne adnotacje:
• @Configuration: Oznacza, że klasa może być używana jako źródło definicji beanów.
• @EnableAutoConfiguration: Umożliwia automatyczną konfigurację aplikacji na podstawie zależności znajdujących się w classpath.
• @ComponentScan: Wskazuje Springowi, aby skanował pakiet, w którym znajduje się ta klasa oraz podpakiety w poszukiwaniu komponentów, serwisów i innych beanów.
2. Metoda main:
− Jest to metoda, która uruchamia aplikację.
− Używa SpringApplication.run(), aby zainicjować kontekst aplikacji Spring i uruchomić serwer aplikacji (domyślnie na porcie 8080).
Podsumowanie:
Klasa ProjektZajavka2Application jest głównym punktem wejścia dla aplikacji opartej na Spring Boot. Umożliwia uruchomienie całej aplikacji oraz korzystanie z mechanizmów automatycznej konfiguracji i zarządzania komponentami oferowanych przez framework Spring. Po uruchomieniu tej klasy, aplikacja zaczyna działać jako serwer aplikacji, gotowy do obsługi żądań.
src/main/resources/application.properties
Opis ustawień:
1. Ustawienia H2:
spring.datasource.url: Ustawia URL bazy danych H2 w pamięci, co oznacza, że baza danych jest przechowywana tylko w RAM i nie jest trwale zapisywana na dysku.
spring.datasource.driverClassName: Wskazuje klasę sterownika dla H2.
spring.datasource.username i spring.datasource.password: Ustawiają dane logowania do bazy danych.
spring.jpa.database-platform: Ustawia platformę dla Hibernate do H2.
spring.h2.console.enabled: Włącza konsolę H2 do monitorowania bazy danych.
 spring.h2.console.path: Określa ścieżkę do konsoli H2, która będzie dostępna pod /h2-console.
2. Konfiguracja Thymeleaf:
spring.thymeleaf.prefix: Ustawia katalog, w którym znajdują się szablony Thymeleaf.
spring.thymeleaf.suffix: Ustawia rozszerzenie plików szablonów.
spring.thymeleaf.mode: Określa tryb działania Thymeleaf, w tym przypadku HTML.
spring.thymeleaf.encoding: Ustawia kodowanie plików szablonów na UTF-8.
spring.thymeleaf.cache: Wyłącza buforowanie szablonów, co jest przydatne w czasie dewelopmentu.

3. Ogólne ustawienia aplikacji:
spring.mvc.throw-exception-if-no-handler-found: Ustawia aplikację, aby zgłaszała wyjątek, jeśli nie znaleziono odpowiedniego handlera dla danego żądania.
spring.resources.add-mappings: Wyłącza automatyczne dodawanie mapowań zasobów, co może być przydatne, jeśli masz niestandardowe mapowania.

4. Ustawienia błędów:
server.error.whitelabel.enabled: Wyłącza domyślną stronę błędu "whitelabel", aby można było zdefiniować własne strony błędów.
   server.error.path: Określa ścieżkę, pod którą będą dostępne strony błędów.
   server.port: Ustawia port, na którym będzie działać aplikacja.

5. Ustawienia dla WireMock:
currency.api.url: Ustawia adres URL dla API walutowego, który będzie używany przez aplikację, wskazując na lokalnego serwera WireMock 

src/main/resources/templates

w projekcie Spring Boot służy do przechowywania szablonów dla warstwy prezentacji, a konkretnie dla silnika szablonów Thymeleaf. Pliki znajdujące się w tym folderze są używane do renderowania widoków w odpowiedzi na żądania HTTP. Oto bardziej szczegółowy opis tego, co może się tam znajdować:
Folder src/main/resources/templates jest kluczowym elementem warstwy web w aplikacji Spring Boot, umożliwiającym tworzenie dynamicznych, interaktywnych widoków. Dzięki Thymeleaf, szablony te są łatwe do zintegrowania z logiką aplikacji, co pozwala na efektywne zarządzanie prezentacją danych użytkownika. 
Oto przykładowe omówienie klasy testowej CategoryServiceTest, która testuje serwis CategoryService w aplikacji. Opis zawiera informacje o celach testów, używanych technikach oraz wynikach.
Opis klasy testowej CategoryServiceTest
Cel klasy
Klasa CategoryServiceTest ma na celu testowanie logiki biznesowej serwisu CategoryService, który zarządza encjami kategorii w aplikacji. Testy jednostkowe w tej klasie sprawdzają poprawność działania metod serwisu oraz ich interakcję z repozytorium CategoryRepository.
Zastosowane adnotacje
• @ExtendWith(MockitoExtension.class): Umożliwia użycie Mockito do mockowania zależności w testach JUnit 5.
• @Mock: Adnotacja do tworzenia mocka dla CategoryRepository, który jest używany przez serwis.
• @InjectMocks: Umożliwia wstrzykiwanie mocków do instancji testowanej klasy (CategoryService).
Testy w klasie
1. Test testFindAllCategories
− Cel: Sprawdzenie, czy metoda findAllCategories poprawnie zwraca wszystkie kategorie.
− Opis:
• Tworzone są przykładowe dane kategorii.
• Mockowane jest zachowanie repozytorium, aby zwracało listę tych kategorii.
• Wywoływana jest metoda serwisu, a następnie sprawdzana jest liczba zwróconych kategorii oraz ich nazwy.
− Oczekiwania:
• Powinno być 2 kategorie w wyniku.
• Nazwy kategorii powinny odpowiadać wprowadzonym wartościom.
2. Test testSaveCategory
− Cel: Sprawdzenie, czy metoda saveCategory poprawnie zapisuje nową kategorię.
− Opis:
• Tworzona jest nowa kategoria do zapisania.
• Mockowane jest repozytorium, aby zwracało tę samą kategorię po zapisaniu.
• Wywoływana jest metoda serwisu, a następnie sprawdzana jest nazwa zapisanej kategorii oraz czy metoda save została wywołana dokładnie raz.
− Oczekiwania:
• Nazwa zapisanej kategorii powinna być "New Category".
3. Test testDeleteCategoryById
− Cel: Sprawdzenie, czy metoda deleteCategoryById poprawnie wywołuje operację usuwania kategorii.
− Opis:
• Wywoływana jest metoda serwisu z identyfikatorem kategorii do usunięcia.
• Sprawdzane jest, czy metoda deleteById repozytorium została wywołana z odpowiednim identyfikatorem.
− Oczekiwania:
• Metoda deleteById powinna być wywołana dokładnie raz z odpowiednim identyfikatorem.
Podsumowanie
Klasa CategoryServiceTest demonstruje dobre praktyki w pisaniu testów jednostkowych, takie jak:
• Izolacja testów: Testowanie serwisu w izolacji od repozytoriów.
• Mockowanie: Użycie mocków do symulacji zachowań repozytoriów.
• Jasne asercje: Sprawdzanie wyników w sposób, który jasno pokazuje, co jest testowane.
Testy te zapewniają, że CategoryService działa zgodnie z oczekiwaniami, co jest kluczowe dla zachowania integralności aplikacji. Każdy test powinien być dokumentowany w dokumentacji projektu, aby inni deweloperzy mogli łatwo zrozumieć, co jest testowane i jakie są oczekiwania.
Opis klasy testowej CategoryRepositoryTest
Cel klasy
Klasa CategoryRepositoryTest ma na celu testowanie funkcjonalności repozytorium CategoryRepository, które zarządza encjami kategorii w aplikacji. Testy jednostkowe w tej klasie sprawdzają, czy operacje na bazie danych, takie jak zapisywanie, znajdowanie i usuwanie kategorii, działają zgodnie z oczekiwaniami.
Zastosowane adnotacje
• @DataJpaTest: Adnotacja ta konfiguruje kontekst aplikacji do testów z użyciem Spring Data JPA, w tym automatycznie konfiguruje bazę danych w pamięci (np. H2) oraz tworzy repozytoria i entity manager. Jest to idealne do testów, które nie wymagają pełnej konfiguracji kontekstu Spring.
Inicjalizacja
• Zmienne do przechowywania identyfikatorów kategorii: Klasa zawiera zmienne electronicsId, booksId i clothingId, które służą do przechowywania identyfikatorów zapisanych kategorii.
• Metoda setUp(): Metoda ta jest wywoływana przed każdym testem, a jej zadaniem jest zapisanie trzech początkowych kategorii w bazie danych. Dzięki temu testy mają dostęp do tych danych, co umożliwia sprawdzenie ich funkcjonalności.
Testy w klasie
1. Test whenFindById_thenReturnCategory
− Cel: Sprawdzenie, czy metoda findById poprawnie zwraca kategorię na podstawie jej identyfikatora.
− Opis:
• Test używa assertThat, aby sprawdzić, czy zwrócona wartość jest obecna (obiekt jest znaleziony) i czy nazwa kategorii odpowiada oczekiwanej wartości ("Electronics").
− Oczekiwania:
• Zwrócona kategoria powinna mieć nazwę "Electronics".
2. Test whenFindAll_thenReturnCategories
− Cel: Sprawdzenie, czy metoda findAll zwraca wszystkie zapisane kategorie.
− Opis:
• Test sprawdza, czy lista kategorii nie jest pusta, czy zawiera trzy elementy i czy nazwy tych kategorii odpowiadają oczekiwanym wartościom ("Electronics", "Books", "Clothing").
− Oczekiwania:
• Lista powinna zawierać dokładnie te trzy kategorie.
3. Test whenSaveCategory_thenCategoryShouldBeSaved
− Cel: Sprawdzenie, czy metoda save poprawnie zapisuje nową kategorię.
− Opis:
• Nowa kategoria ("Home & Garden") jest zapisywana w repozytorium, a następnie test sprawdza, czy obiekt nie jest pusty oraz czy jego nazwa odpowiada oczekiwanemu rezultatowi.
• Dodatkowo testuje się, czy zapisana kategoria jest dostępna w repozytorium za pomocą metody findById.
− Oczekiwania:
• Kategoria powinna być zapisana i dostępna z odpowiednią nazwą.
4. Test whenDeleteCategory_thenCategoryShouldBeDeleted
− Cel: Sprawdzenie, czy metoda deleteById poprawnie usuwa kategorię.
− Opis:
• Kategoria ("Toys") jest najpierw zapisywana, a następnie usuwana z repozytorium. Test sprawdza, czy po usunięciu nie jest już obecna w repozytorium.
− Oczekiwania:
• Kategoria powinna być usunięta i nie powinna być dostępna w repozytorium.
Podsumowanie
Klasa CategoryRepositoryTest stanowi przykład dobrych praktyk w pisaniu testów jednostkowych dla repozytoriów w aplikacji Spring. Wykorzystanie adnotacji takich jak @DataJpaTest oraz narzędzi do asercji (AssertJ) sprawia, że testy są czytelne i zrozumiałe. Każdy test jest jasno określony, co pozwala na łatwe zrozumienie, co jest testowane i jakie są oczekiwania.
Takie podejście pozwala na szybkie weryfikowanie poprawności działania warstwy dostępu do danych i zapewnia, że repozytorium działa zgodnie z założeniami. Dobrze udokumentowane testy ułatwiają innym deweloperom zrozumienie logiki aplikacji oraz ułatwiają wprowadzanie ewentualnych zmian w przyszłości.
Opis klasy testowej CategoryControllerTest
Cel klasy
Klasa CategoryControllerTest ma na celu testowanie kontrolera CategoryController, który zarządza żądaniami HTTP związanymi z encjami kategorii. Testy jednostkowe w tej klasie sprawdzają, czy kontroler poprawnie reaguje na różne operacje, takie jak pobieranie listy kategorii, wyświetlanie formularza nowej kategorii, zapisywanie kategorii oraz usuwanie kategorii.
Zastosowane adnotacje
• @WebMvcTest(CategoryController.class): Ta adnotacja konfiguruje kontekst aplikacji do testów kontrolera, automatycznie konfiguruje MockMvc oraz ogranicza kontekst do komponentów związanych z warstwą webową.
• @WithMockUser(username = "testuser", roles = {"ADMIN"}): Adnotacja ta symuluje zalogowanego użytkownika z rolą "ADMIN", co pozwala na testowanie zabezpieczeń kontrolera.
Inicjalizacja
• Obiekt MockMvc: Obiekt ten jest wstrzykiwany za pomocą adnotacji @Autowired i pozwala na symulowanie żądań HTTP oraz sprawdzanie odpowiedzi.
• Mock CategoryService: Użycie adnotacji @MockBean pozwala na tworzenie mocka serwisu CategoryService, co umożliwia kontrolowanie zachowań tego serwisu w testach.
Testy w klasie
1. Test testGetAllCategories
− Cel: Sprawdzenie, czy metoda getAllCategories w kontrolerze poprawnie zwraca listę kategorii.
− Opis:
• Test tworzy dwie kategorie i mockuje odpowiedź serwisu CategoryService, aby zwracał tę listę.
• Następnie wysyła żądanie GET na ścieżkę /categories i sprawdza, czy status odpowiedzi to 200 (OK), a także czy atrybut modelu categories jest obecny i czy widok to categories/list.
− Oczekiwania:
• Oczekiwany status odpowiedzi: 200 (OK).
• Oczekiwany widok: "categories/list".
2. Test testShowNewCategoryForm
− Cel: Sprawdzenie, czy kontroler poprawnie wyświetla formularz do tworzenia nowej kategorii.
− Opis:
• Test wysyła żądanie GET na ścieżkę /categories/new i sprawdza, czy odpowiedź ma status 200 (OK) oraz czy widok to categories/form. Dodatkowo testuje, czy w modelu znajduje się atrybut category.
− Oczekiwania:
• Oczekiwany status odpowiedzi: 200 (OK).
• Oczekiwany widok: "categories/form".
3. Test testSaveCategory
− Cel: Sprawdzenie, czy metoda saveCategory w kontrolerze poprawnie zapisuje nową kategorię.
− Opis:
• Test symuluje żądanie POST do /categories z parametrem name ustawionym na "New Category" oraz dodaje token CSRF dla bezpieczeństwa.
• Sprawdza, czy odpowiedź ma status 3xx (przekierowanie) oraz czy przekierowuje do /categories.
• Weryfikuje, czy metoda saveCategory w serwisie została wywołana z odpowiednim obiektem Category.
− Oczekiwania:
• Oczekiwany status odpowiedzi: 3xx (przekierowanie).
• Oczekiwany widok po przekierowaniu: "/categories".
4. Test testDeleteCategory
− Cel: Sprawdzenie, czy metoda deleteCategory w kontrolerze poprawnie usuwa kategorię.
− Opis:
• Test symuluje żądanie DELETE do /categories/delete/1 z dodanym tokenem CSRF.
• Sprawdza, czy odpowiedź ma status 3xx (przekierowanie) oraz czy przekierowuje do /categories.
• Weryfikuje, czy metoda deleteCategoryById w serwisie została wywołana z odpowiednim identyfikatorem.
− Oczekiwania:
• Oczekiwany status odpowiedzi: 3xx (przekierowanie).
• Oczekiwany widok po przekierowaniu: "/categories".
Podsumowanie
Klasa CategoryControllerTest jest przykładem efektywnego testowania kontrolera w aplikacji Spring. Wykorzystanie MockMvc umożliwia symulowanie rzeczywistych żądań HTTP i weryfikację odpowiedzi, co pozwala na testowanie funkcjonalności kontrolera bez potrzeby uruchamiania całej aplikacji.
Każdy test jest jasno określony, co pozwala na szybkie zrozumienie, co jest testowane i jakie są oczekiwania. Dodatkowo, testy te pomagają w weryfikacji, czy logika kontrolera jest zgodna z wymaganiami oraz czy interakcje z warstwą serwisu działają prawidłowo.
Dzięki zastosowaniu mocków i symulacji użytkowników, klasa testowa jest niezależna od rzeczywistych implementacji i danych, co zwiększa jej wydajność i niezawodność.
Opis klasy testowej CategoryRestControllerTest
Cel klasy
Klasa CategoryRestControllerTest ma na celu testowanie działania kontrolera REST CategoryRestController, który obsługuje żądania związane z encjami kategorii w aplikacji. Testy jednostkowe w tej klasie weryfikują, czy endpointy API działają poprawnie, zapewniając odpowiednią obsługę żądań dla różnych operacji CRUD (tworzenie, odczyt, aktualizacja, usuwanie).
Zastosowane adnotacje
• @SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT): Uruchamia kontekst aplikacji w trybie testowym na losowym porcie, co pozwala na testowanie aplikacji w bardziej zbliżonym do rzeczywistego środowisku.
• @AutoConfigureMockMvc: Automatycznie konfiguruje MockMvc, umożliwiając symulowanie żądań HTTP w testach.
• @Transactional: Oznacza, że każdy test będzie działał w ramach transakcji, która jest automatycznie wycofywana po zakończeniu testu, co zapobiega modyfikacji bazy danych.
Inicjalizacja
• Obiekt ObjectMapper: Używany do konwertowania obiektów Java na JSON i odwrotnie.
• @LocalServerPort: Wstrzykuje losowy port, na którym działa aplikacja.
• Repozytoria: Wstrzykiwane są repozytoria CategoryRepository, RestaurantRepository i MenuItemRepository, co umożliwia interakcję z danymi w bazie.
• Obiekty Restaurant, MenuItem i Category: Te encje są używane do testowania funkcjonalności kontrolera.
• Obiekt MockMvc: Umożliwia symulowanie żądań HTTP do kontrolera i sprawdzanie odpowiedzi.
Metoda setUp
W metodzie setUp przygotowywane są dane testowe:
• Tworzona jest nowa kategoria o nazwie "Test Category", która jest zapisywana w bazie danych.
Testy w klasie
1. Test testGetAllCategories
− Cel: Sprawdzenie, czy endpoint GET /api/categories poprawnie zwraca listę kategorii.
− Opis:
• Wysyłane jest żądanie GET na ścieżkę /api/categories.
• Oczekiwany status odpowiedzi to 200 (OK), oraz że w odpowiedzi znajduje się jedna kategoria o nazwie "Test Category".
− Oczekiwania:
• Status: 200 (OK).
• Liczba kategorii: 1.
• Nazwa kategorii: "Test Category".
2. Test testCreateAndGetCategory
− Cel: Sprawdzenie, czy można utworzyć nową kategorię i czy jest ona dostępna w bazie danych.
− Opis:
• Tworzona jest nowa restauracja i nowa kategoria.
• Wysyłane jest żądanie POST do /api/categories w celu utworzenia nowej kategorii.
• Oczekiwany status to 201 (Created) oraz, że nowa kategoria została poprawnie utworzona.
• Następnie sprawdzane jest, czy nowa kategoria znajduje się w liście kategorii.
− Oczekiwania:
• Status: 201 (Created).
• Kategoria powinna być widoczna w wynikach GET.
3. Test testUpdateCategory
− Cel: Sprawdzenie, czy można zaktualizować istniejącą kategorię.
− Opis:
• Przygotowywane są nowe dane dla kategorii.
• Wysyłane jest żądanie PUT do /api/categories/{id} w celu zaktualizowania kategorii.
• Oczekiwany status to 200 (OK) oraz nowa nazwa kategorii.
• Dodatkowo, weryfikowane jest, czy kategoria została zaktualizowana w bazie danych.
− Oczekiwania:
• Status: 200 (OK).
• Nowa nazwa kategorii w bazie danych.
4. Test testDeleteCategory
− Cel: Sprawdzenie, czy można usunąć istniejącą kategorię.
− Opis:
• Sprawdzane jest, czy kategoria istnieje przed próbą jej usunięcia.
• Wysyłane jest żądanie DELETE do /api/categories/{id} w celu usunięcia kategorii.
• Oczekiwany status to 204 (No Content).
• Po usunięciu, ponownie sprawdzane jest, czy kategoria została usunięta z bazy danych.
− Oczekiwania:
• Status: 204 (No Content).
• Lista kategorii powinna być pusta po usunięciu.
Podsumowanie
Klasa CategoryRestControllerTest skutecznie testuje działanie kontrolera REST, zapewniając, że endpointy API zachowują się zgodnie z oczekiwaniami. Dzięki zastosowaniu MockMvc można symulować żądania HTTP i weryfikować odpowiedzi, co jest kluczowe w testowaniu aplikacji webowych.
Obejmuje to testowanie wszystkich podstawowych operacji CRUD dla encji kategorii, co pozwala na szybkie wykrywanie błędów i potwierdzanie poprawności działania aplikacji.
Zastosowanie adnotacji do mockowania użytkownika oraz transakcyjności testów umożliwia testowanie logiki kontrolera w sposób izolowany i niezawodny, co jest istotne w kontekście aplikacji opartych na architekturze mikroserwisów i RESTful API.
Opis klasy testowej CategoryControllerIntegrationTest
Cel klasy
Klasa CategoryControllerIntegrationTest ma na celu przeprowadzanie testów integracyjnych dla kontrolera kategorii w aplikacji. Skupia się na weryfikacji poprawności działania endpointów związanych z zarządzaniem kategoriami, takich jak pobieranie wszystkich kategorii, tworzenie nowych kategorii oraz usuwanie istniejących.
Zastosowane adnotacje
• @SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT): Uruchamia kontekst aplikacji w trybie testowym, co pozwala na testowanie w zbliżonym do rzeczywistego środowisku. Używa losowego portu, co eliminuje konflikty z innymi aplikacjami.
• @Transactional: Oznacza, że każdy test będzie działał w kontekście transakcji, która zostanie automatycznie wycofana po zakończeniu testu, co zapobiega wprowadzaniu niepożądanych zmian w bazie danych.
• @AutoConfigureMockMvc: Automatycznie konfiguruje MockMvc, co umożliwia symulowanie żądań HTTP w testach.
Inicjalizacja
• Obiekt MockMvc: Umożliwia wykonywanie żądań HTTP i weryfikację odpowiedzi bez uruchamiania serwera.
• Repozytorium CategoryRepository: Umożliwia dostęp do danych kategorii w bazie danych.
Metoda setUp
W metodzie setUp przygotowywane są dane testowe:
• Tworzona jest nowa kategoria o nazwie "Test Category", która jest zapisywana w bazie danych. Umożliwia to przetestowanie operacji na istniejących kategoriach.
Testy w klasie
1. Test testGetAllCategories
− Cel: Sprawdzenie, czy endpoint GET /categories zwraca poprawne dane.
− Opis:
• Wysyłane jest żądanie GET na endpoint /categories.
• Oczekiwany status odpowiedzi to 200 (OK), oraz że widok odpowiada categories/list.
• Oczekiwane jest również, że w modelu znajduje się atrybut categories z jedną kategorią o nazwie "Test Category".
− Oczekiwania:
• Status: 200 (OK).
• Widok: categories/list.
• Atrybut categories zawiera jedną kategorię o nazwie "Test Category".
2. Test testShowNewCategoryForm
− Cel: Sprawdzenie, czy formularz do tworzenia nowej kategorii jest poprawnie wyświetlany.
− Opis:
• Wysyłane jest żądanie GET na endpoint /categories/new.
• Oczekiwany status to 200 (OK), a widok to categories/form.
• Model powinien zawierać atrybut category.
− Oczekiwania:
• Status: 200 (OK).
• Widok: categories/form.
• Atrybut category istnieje w modelu.
3. Test testSaveCategory
− Cel: Sprawdzenie, czy nowa kategoria może być poprawnie zapisana w bazie danych.
− Opis:
• Wysyłane jest żądanie POST do endpointu /categories z parametrem name równym "Desserts".
• Oczekiwany status odpowiedzi to 3xx (przekierowanie), a adres przekierowania to /categories.
• Po zapisaniu, test weryfikuje, czy kategoria o nazwie "Desserts" została rzeczywiście zapisana w bazie.
− Oczekiwania:
• Status: 3xx (przekierowanie).
• Przekierowanie na /categories.
• Kategoria "Desserts" powinna istnieć w bazie danych.
4. Test testDeleteCategory
− Cel: Sprawdzenie, czy istniejąca kategoria może być poprawnie usunięta.
− Opis:
• Pobierane są wszystkie kategorie, aby upewnić się, że istnieje co najmniej jedna do usunięcia.
• Wysyłane jest żądanie DELETE na endpoint /categories/delete/{id} dla kategorii, której ID zostało pobrane.
• Oczekiwany status to 3xx (przekierowanie) na adres /categories.
• Po usunięciu kategorie, test weryfikuje, czy liczba kategorii w repozytorium wynosi 0.
− Oczekiwania:
• Status: 3xx (przekierowanie).
• Przekierowanie na /categories.
• Liczba kategorii powinna wynosić 0.
Podsumowanie
Klasa CategoryControllerIntegrationTest skutecznie testuje funkcjonalność kontrolera kategorii, zapewniając, że wszystkie podstawowe operacje związane z zarządzaniem kategoriami działają poprawnie.
Zastosowanie MockMvc pozwala na symulowanie rzeczywistych żądań HTTP i weryfikację odpowiedzi, co jest istotne w kontekście aplikacji webowych.
Dzięki adnotacji do mockowania użytkownika oraz transakcyjności testów, możliwe jest testowanie logiki kontrolera w sposób izolowany i niezawodny. Takie podejście ułatwia również identyfikację potencjalnych błędów w logice aplikacji oraz przyspiesza proces wprowadzania zmian.

Wszystkie pozostałe klasy testowe zostały napisane w podobny sposób jak opisana klasa powyżej 
Klasa CurrencyServiceTest użyty serwer WireMock:
• wireMockServer = new WireMockServer(8080);
• Serwer WireMock jest uruchamiany na porcie 8080, co symuluje działanie zewnętrznego serwisu wymiany walut.
Definiowanie stubów (reguł) dla serwera WireMock:
• wireMockServer.stubFor(...)
• Ta konfiguracja mówi WireMockowi, jak ma reagować na określone żądania. W tym przypadku:
wireMockServer.stubFor(get(urlEqualTo("/exchangerates/rates/A/USD?format=json"))            .willReturn(aResponse()
                    .withStatus(200)
                    .withBody("{ \"rates\": [{ \"mid\": \"4.05\" }] }")));
Kiedy ktoś (np. CurrencyService) wyśle żądanie GET na endpoint /exchangerates/rates/A/USD?format=json, WireMock odpowie statusem 200 OK i zwróci ciało odpowiedzi:
 { "rates": [{ "mid": "4.05" }] }
Tworzenie instancji CurrencyService:
• currencyService = new CurrencyService(restTemplate, "http://localhost:8080", objectMapper);
• Tworzona jest instancja CurrencyService, z której korzystają testy. Wstrzykuje się do niej RestTemplate, URL do symulowanego serwera (http://localhost:8080), oraz ObjectMapper.
4. Metoda testGetUsdExchangeRate():
Testuje metodę getUsdExchangeRate() w serwisie CurrencyService.
• Wywołanie metody getUsdExchangeRate():
− String rate = currencyService.getUsdExchangeRate();
− Serwis CurrencyService wykonuje zapytanie na zewnętrzne API (w tym przypadku do WireMock), a odpowiedź ({ "rates": [{ "mid": "4.05" }] }) jest przetwarzana przez CurrencyService.
• Porównanie wyniku z oczekiwaną wartością:
− assertEquals("4.05", rate);
− Sprawdza, czy wartość zwrócona przez metodę to "4.05", co jest oczekiwanym wynikiem na podstawie stubu zdefiniowanego w WireMock.
5. Metoda tearDown():
Zatrzymuje serwer WireMock po każdym teście:
• wireMockServer.stop();
− Dzięki temu środowisko testowe jest czyszczone po zakończeniu testu, a serwer przestaje nasłuchiwać na porcie 8080.
Podsumowanie:
Ta klasa testowa wykorzystuje WireMock do symulacji odpowiedzi z zewnętrznego API oraz Spring Boot do testowania integracji CurrencyService. Główne kroki to:
1. Uruchomienie serwera WireMock i zdefiniowanie jego zachowania.
2. Przeprowadzenie testu metody getUsdExchangeRate(), która pobiera kurs dolara z symulowanego serwera.
3. Porównanie wyniku z oczekiwaną wartością.
4. Zatrzymanie serwera WireMock po zakończeniu testu.
Oto opis klasy CurrencyControllerTest:
1. Cel klasy:
• Klasa ta jest testem kontrolera (CurrencyController), który zwraca kurs dolara (USD) z serwisu CurrencyService. Test sprawdza, czy kontroler poprawnie obsługuje żądania HTTP i zwraca oczekiwane odpowiedzi w formacie JSON.
2. Adnotacje użyte w klasie:
• @WebMvcTest(CurrencyController.class):
− Adnotacja ta konfiguruje Springa do testowania tylko warstwy kontrolera (CurrencyController), ignorując inne komponenty aplikacji, takie jak warstwa serwisowa czy repozytoria.
− Dzięki tej adnotacji, Spring ładuje tylko kontekst Web MVC, co przyspiesza testy i ogranicza zależności.
• @Autowired:
− Służy do wstrzykiwania komponentów Springa, takich jak MockMvc, który jest używany do symulowania i testowania żądań HTTP do kontrolera.
• @MockBean:
− @MockBean tworzy atrapę serwisu CurrencyService, co oznacza, że podczas testu nie będzie używany rzeczywisty serwis.
− Wszystkie wywołania do currencyService są symulowane, co pozwala na pełną kontrolę nad tym, jakie dane zwracają metody serwisu w trakcie testów.
− W tym teście użyto tej adnotacji, aby symulować odpowiedź metody getUsdExchangeRate() w CurrencyService.
3. Zdefiniowane pola:
• MockMvc mockMvc:
− Kluczowy komponent używany do testowania kontrolera.
− MockMvc pozwala na symulowanie żądań HTTP do kontrolera oraz na weryfikowanie odpowiedzi (statusu, zawartości itp.).
• CurrencyService currencyService:
− @MockBean tworzy atrapę tego serwisu.
− Używane do symulowania odpowiedzi metody getUsdExchangeRate() w trakcie testu.
4. Metoda testGetUsdRate():
Jest to właściwy test kontrolera CurrencyController.
• @WithMockUser(username = "testuser", roles = {"ADMIN"}):
− Symuluje użytkownika o nazwie testuser z rolą ADMIN podczas testowania.
− Umożliwia testowanie kontrolera, który może wymagać autoryzacji lub określonej roli do wykonania żądania.
• Ustawienie oczekiwanego wyniku:
− String expectedRate = "4.25";
− Wartość 4.25 jest ustawiana jako kurs dolara, który serwis CurrencyService zwróci w trakcie testu.
• Symulowanie odpowiedzi serwisu CurrencyService:
when(currencyService.getUsdExchangeRate()).thenReturn(expectedRate);
• Gdy kontroler wywoła metodę getUsdExchangeRate() na serwisie currencyService, zwróci ona wartość "4.25".

•  Symulowanie żądania HTTP GET:
.andExpect(status().isOk())
.andExpect(content().contentType("application/json"))
.andExpect(content().json("{\"rate\":\"" + expectedRate + "\"}"));
  .andExpect(status().isOk()): Sprawdza, czy odpowiedź ma status HTTP 200 OK.
  .andExpect(content().contentType("application/json")): Sprawdza, czy typ zawartości odpowiedzi to application/json.
  .andExpect(content().json("{\"rate\":\"" + expectedRate + "\"}")):
• Sprawdza, czy odpowiedź JSON ma postać:
{
  "rate": "4.25"
}
Użycie expectedRate dynamicznie wstawia wartość "4.25" do odpowiedzi JSON, co jest zgodne z ustawionym wcześniej wynikiem.
5. Podsumowanie:
• Klasa CurrencyControllerTest sprawdza, czy kontroler CurrencyController zwraca oczekiwaną odpowiedź JSON po wywołaniu endpointu /api/usd-rate.
• Test:
1. Symuluje użytkownika z rolą ADMIN.
2. Konfiguruje atrapę serwisu CurrencyService, aby zwracała określony kurs dolara (4.25).
3. Wysyła żądanie GET do kontrolera (/api/usd-rate).
4. Sprawdza odpowiedź, upewniając się, że:
• Status odpowiedzi to 200 OK.
• Typ zawartości to application/json.
• Zawartość JSON to {"rate": "4.25"}.
Ten test jest przykładem testu jednostkowego kontrolera z użyciem MockMvc i atrap serwisu (@MockBean), co pozwala testować zachowanie kontrolera bez potrzeby uruchamiania rzeczywistych serwisów backendowych.

Plik Dockerfile służy do budowania obrazu Dockera dla aplikacji opartej na Javie. Oto wyjaśnienie poszczególnych kroków:
Bazowy obraz:
Obraz openjdk:17-jdk-alpine to lekki obraz z Javą 17 (OpenJDK) oparty na Alpine Linux, co sprawia, że jest szybki i mały.
Ustawienie katalogu roboczego:
Komenda WORKDIR /app ustawia katalog roboczy w kontenerze na /app, gdzie będą umieszczone pliki aplikacji.
Kopiowanie plików JAR:
COPY target/projektZajavka2.jar app.jar kopiuje plik JAR z katalogu target (generowany po zbudowaniu projektu) do kontenera, nazywając go app.jar.
Otwarcie portu aplikacji:
EXPOSE 8085 informuje Dockera, że aplikacja będzie działać na porcie 8085. Ten port jest "otwarty" dla połączeń z zewnątrz.
Komenda uruchamiająca aplikację:
ENTRYPOINT ["java", "-jar", "app.jar"] to komenda, która uruchamia aplikację Java z pliku JAR. Gdy kontener zostanie uruchomiony, aplikacja startuje automatycznie.
W skrócie, ten plik konfiguruje obraz Dockera z Javą 17, kopiuje aplikację, otwiera odpowiedni port, a na końcu uruchamia aplikację.
Plik plik docker-compose.yml definiuje konfigurację dla dwóch usług w kontenerach Docker: aplikacji Spring Boot oraz WireMocka. Oto krótkie wyjaśnienie:
Usługa app (Aplikacja Spring Boot):
build: Aplikacja zostanie zbudowana na podstawie pliku Dockerfile w bieżącym katalogu.
image: Zostanie utworzony obraz o nazwie projektzajavka2:latest.
ports: Port aplikacji 8085 na maszynie lokalnej zostanie zmapowany na port 8085 w kontenerze (aplikacja działa na porcie 8085).
environment: Zmienna środowiskowa SPRING_PROFILES_ACTIVE zostanie ustawiona na "docker", co pozwala aplikacji na uruchomienie w odpowiednim profilu.
depends_on: Aplikacja zależy od usługi wiremock, co oznacza, że uruchomienie aplikacji nastąpi po uruchomieniu WireMocka.
networks: Aplikacja korzysta z sieci spring-boot-network.

Usługa wiremock (WireMock):
image: Używany jest oficjalny obraz Docker dla WireMocka o nazwie wiremock/wiremock:latest.
command: WireMock uruchamiany z opcją --verbose (szczegółowe logi) i --local-response-templating (włącza szablonowanie odpowiedzi).
networks: WireMock również korzysta z tej samej sieci spring-boot-network, co aplikacja, aby mogły się komunikować.

Sieć spring-boot-network:
Sieć typu bridge, która pozwala na komunikację między usługami aplikacji Spring Boot i WireMocka w ramach tego samego projektu Docker.

To zapewnia izolację oraz łatwość komunikacji między kontenerami, a także ułatwia testowanie aplikacji z użyciem WireMocka.

Zachowanie aplikacji po uruchomieniu:

:: Spring Boot ::                (v3.3.3)

2024-10-13T17:24:35.141+02:00  INFO 14760 --- [           main] p.ProjektZajavka2Application             : Starting ProjektZajavka2Application using Java 22.0.1 with PID 14760 (D:\java nauka\projektZajavka2\target\classes started by L.M in D:\java nauka\projektZajavka2)
2024-10-13T17:24:35.149+02:00  INFO 14760 --- [           main] p.ProjektZajavka2Application             : The following 1 profile is active: "h2"
2024-10-13T17:24:36.023+02:00  INFO 14760 --- [           main] .s.d.r.c.RepositoryConfigurationDelegate : Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2024-10-13T17:24:36.112+02:00  INFO 14760 --- [           main] .s.d.r.c.RepositoryConfigurationDelegate : Finished Spring Data repository scanning in 80 ms. Found 8 JPA repository interfaces.
2024-10-13T17:24:36.853+02:00  INFO 14760 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port 8085 (http)
2024-10-13T17:24:36.872+02:00  INFO 14760 --- [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2024-10-13T17:24:36.872+02:00  INFO 14760 --- [           main] o.apache.catalina.core.StandardEngine    : Starting Servlet engine: [Apache Tomcat/10.1.28]
2024-10-13T17:24:36.971+02:00  INFO 14760 --- [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2024-10-13T17:24:36.972+02:00  INFO 14760 --- [           main] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 1760 ms
2024-10-13T17:24:37.010+02:00  INFO 14760 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2024-10-13T17:24:37.263+02:00  INFO 14760 --- [           main] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Added connection conn0: url=jdbc:h2:mem:testdb user=SA
2024-10-13T17:24:37.267+02:00  INFO 14760 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Start completed.
2024-10-13T17:24:37.281+02:00  INFO 14760 --- [           main] o.s.b.a.h2.H2ConsoleAutoConfiguration    : H2 console available at '/h2-console'. Database available at 'jdbc:h2:mem:testdb'
2024-10-13T17:24:37.582+02:00  INFO 14760 --- [           main] o.hibernate.jpa.internal.util.LogHelper  : HHH000204: Processing PersistenceUnitInfo [name: default]
2024-10-13T17:24:37.641+02:00  INFO 14760 --- [           main] org.hibernate.Version                    : HHH000412: Hibernate ORM core version 6.5.2.Final
2024-10-13T17:24:37.681+02:00  INFO 14760 --- [           main] o.h.c.internal.RegionFactoryInitiator    : HHH000026: Second-level cache disabled
2024-10-13T17:24:38.033+02:00  INFO 14760 --- [           main] o.s.o.j.p.SpringPersistenceUnitInfo      : No LoadTimeWeaver setup: ignoring JPA class transformer
2024-10-13T17:24:38.076+02:00  WARN 14760 --- [           main] org.hibernate.orm.deprecation            : HHH90000025: H2Dialect does not need to be specified explicitly using 'hibernate.dialect' (remove the property setting and it will be selected by default)
2024-10-13T17:24:39.134+02:00  INFO 14760 --- [           main] o.h.e.t.j.p.i.JtaPlatformInitiator       : HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)
2024-10-13T17:24:39.200+02:00  INFO 14760 --- [           main] j.LocalContainerEntityManagerFactoryBean : Initialized JPA EntityManagerFactory for persistence unit 'default'
2024-10-13T17:24:39.821+02:00  WARN 14760 --- [           main] JpaBaseConfiguration$JpaWebConfiguration : spring.jpa.open-in-view is enabled by default. Therefore, database queries may be performed during view rendering. Explicitly configure spring.jpa.open-in-view to disable this warning
2024-10-13T17:24:39.847+02:00  INFO 14760 --- [           main] r$InitializeUserDetailsManagerConfigurer : Global AuthenticationManager configured with UserDetailsService bean with name customUserDetailsService
2024-10-13T17:24:40.803+02:00  INFO 14760 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port 8085 (http) with context path '/'
2024-10-13T17:24:40.813+02:00  INFO 14760 --- [           main] p.ProjektZajavka2Application             : Started ProjektZajavka2Application in 6.321 seconds (process running for 6.812)

Po starcie aplikacji Spring Boot, następuje kilka kluczowych kroków:

Uruchomienie aplikacji: Aplikacja jest uruchamiana z pliku głównego, w tym przypadku ProjektZajavka2Application, co jest wskazywane przez logi zaczynające się od „Starting ProjektZajavka2Application”.

Wykrywanie aktywnego profilu: Aplikacja używa profilu „h2”, co oznacza, że będzie korzystać z wbudowanej bazy danych H2 do testów i operacji bazodanowych.

Inicjalizacja Spring Data JPA: Spring uruchamia konfigurację JPA, co pozwala na używanie repozytoriów i zarządzanie encjami, jak wskazuje log „Bootstrapping Spring Data JPA repositories”. To oznacza, że Spring szuka klas repozytoriów, które będą używane do pracy z bazą danych.

Przygotowanie komponentów aplikacji: Spring Boot konfiguruje inne komponenty, takie jak zarządzanie połączeniami bazodanowymi, mechanizmy bezpieczeństwa (jeśli są skonfigurowane) oraz serwer Tomcat (domyślny serwer wbudowany), aby aplikacja mogła obsługiwać żądania HTTP.

Na końcu aplikacja jest gotowa do przyjmowania zapytań i działa w pełni.

