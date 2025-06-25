# Scryfall Data Visualization Sandbox

## 1. Overview

The Scryfall Data Visualization Sandbox is a powerful, single-page web application designed for *Magic: The Gathering* players, collectors, and data enthusiasts. It allows users to perform any valid Scryfall search query and instantly generate a dashboard of custom, interactive charts to visualize the results.

This tool is built entirely within a single HTML file, leveraging the Scryfall API for data, D3.js for charting, and Tailwind CSS for a modern, responsive user interface.

## 2. Core Features

### Search & Data Fetching

* **Universal Scryfall Search:** Utilizes the full power of the Scryfall search syntax (e.g., `t:goblin year>=2021`, `cmc=1 pow>3`).
* **Paginated Fetching:** Automatically handles paginated API results to load complete datasets.
* **Rate-Limit Respectful:** A built-in 100ms delay between paged requests ensures compliance with Scryfall's API guidelines.
* **Visual Progress Bar:** A smooth progress bar and card counter provide real-time feedback on the data loading process.

### Dynamic Chart Builder

* **Auto-Populated Properties:** After a search, the "Data Property" dropdown is automatically filled with all valid properties found on the fetched cards, including arrays and inferred types.
* **Multiple Chart Types:** Supports creating **Bar Charts** and **Donut Charts**.
* **Inferred Properties from Type Line:** The application automatically parses the `type_line` of each card to create new, chartable properties:
    * `inferred_supertypes`: (e.g., Legendary, Snow, Kindred).
    * `inferred_card_types`: (e.g., Creature, Instant, Artifact).
    * `inferred_subtypes`: (e.g., Goblin, Elf, Dragon).
* **Advanced Array Handling:** A dedicated "Array Handling" menu appears for array properties, allowing for nuanced analysis:
    * **Flatten:** Counts each element in an array individually.
    * **Combine:** Groups items by the exact combination of elements.
    * **Summarize:** A special mode for `colors` and `color_identity` that groups cards into "Colorless", "Multicolor", or their single color.
* **Customizable Category Limit:** Users can set the "Top N" categories to display on charts.

### Interactive Chart Dashboard

* **Responsive Grid Layout:** Charts are added to a responsive grid that adapts to any screen size.
* **Live Chart Customization:** Each chart features a **Customize** panel (sliders icon) for real-time adjustments:
    * **Visibility Toggles:** Hide or show specific categories (e.g., remove "None" from a keywords chart) with a single click.
    * **Custom Color Mapping:** Assign custom colors to any category using an intuitive color picker.
* **Chart Management:**
    * **Pin Chart:** Pinned charts (bookmark icon) are preserved across new searches, allowing for data comparison.
    * **Delete Chart:** Easily remove charts from the dashboard.
* **Interactive Tooltips:** Hovering over any chart segment reveals a detailed tooltip with the exact count and percentage.
* **Data Drill-Down:** Clicking on any bar or pie slice opens a modal window displaying a scrollable gallery of all cards belonging to that category.
* **External Links:** Clicking a card image in the gallery opens its official Scryfall page in a new tab.

## 3. How to Use

1.  **Access the Application:** Visit the live version at [https://sejomacode.github.io/ScryfallVisualizer/](https://sejomacode.github.io/ScryfallVisualizer/).
2.  **Perform a Search:** Enter a valid Scryfall query into the search bar and click "Search".
3.  **Build a Chart:**
    * Once the data is loaded, the **Chart Builder** will appear.
    * Select a **Chart Type** (Bar or Donut).
    * Choose a **Data Property** from the dropdown. This list includes raw card properties and the `inferred_` properties.
    * If the property is an array (like `keywords` or `colors`), select an **Array Handling** mode.
    * Optionally, set a **Category Limit** and a **Chart Title**.
    * Click "Add Chart".
4.  **Customize and Analyze:**
    * Use the **pin** and **delete** icons on a chart to manage your dashboard.
    * Click the **customize** (sliders) icon to open the side panel.
    * In the panel, use the checkboxes to hide noisy categories or use the color pickers to re-color segments. The chart will update live.
    * Hover over chart segments for tooltips and click them to see the associated cards.

## 4. Technologies Used

* **HTML5:** For the core structure of the application.
* **Tailwind CSS:** For all styling and the responsive, dark-themed user interface.
* **JavaScript (ES6+):** For all application logic, API interaction, and DOM manipulation.
* **D3.js:** For all data visualization and chart rendering.
* **Scryfall API:** As the data source for all *Magic: The Gathering* card information.
