# WordPress Plugins & More

## Scope of the session

Sometimes it is needed to customize the CSS manually. This session will address methods that help achieving this.

# Update a custom website with WordPress and Docker

### Ways of adding custom CSS to your wp site

- One option is to modify the `style.css` (and other files with css extension) from Appearance -> Theme Editor. Note that your changes may be reverted by an eventual theme update. You can also create a custom file to overwrite given behaviors, which is a safer way.
- Another way is to write inline css directly into your pages' php code.
- The third version would be to use dedicated plugins to alter the css of the project.
- The last solution (which we would use in this session) is to add CSS code to your theme at Appearance -> Customize -> Additional CSS. It is good practice to look for existing classes to override and use them as selectors in the left panel.

> Note: We will use posts in this section, so make sure to check [this](https://www.youtube.com/watch?v=kN3d69Nii-Y) and [that](https://www.youtube.com/watch?v=yqooiG3tDpk) video about posts before getting started. The basic idea is that pages are separate entities from a style and structure perspective, whereas posts are instances of the same entity with different content.

## Step 1: Extending your page

Create two categories (`Expo` and `News`) and add some posts to each of them. You will find some texts at the end of this file to use for those posts.

## Step 2: Add custom CSS to your posts

- Navigate to Appearance -> Customize -> Additional CSS and to the list of posts. Inspect the class for the title of each post and add a custom css so that only the posts categorized as `Expo` will have a title with `blue color`. In order to achieve this, you can write something like:

```css
.category-expo .entry-title {
  color: #ff0000;
}
```

- Secondly, tweak the text so that it is `Bold` (font-weight of 700) only on mobile phones. In web browser, it should stay regular (font-weight of 400).

## Step 3 (Optional): Displaying the post categories in the footer

At widgets, add the categories to the footer.

## Step 4 (Optional): Displaying only a given category

Make changes to the home page so that it displays a list of posts belonging to the category `News`. Other posts should not be displayed on this level.

## Text content for the posts

### News

#### 2022 Hyundai Kona Will Get Styling Updates, N-Line Model

A facelifted version of the Hyundai Kona should be coming to the U.S. soon, if these photos of the Europe-market Kona are any indication. We expect the 2022 Kona to incorporate similar changes when it arrives on our shores, including updated styling inside and out and a new N-Line model with a bit of extra sporting character and a horsepower boost.
<br>
The N-Line, pictured above in red, backs up its slightly more aggressive looks with a more powerful engine, a turbocharged 1.6-liter inline-four with 195 horsepower. That's 20 hp more than the current U.S.-market Kona with this engine, which is currently offered on Limited and Ultimate trims. The standard model, shown here in blue, is likely to continue with its naturally aspirated 2.0-liter inline-four with 147 horsepower. We've also spotted a full-bore Kona N testing, but we might have to wait a bit longer for that performance model to arrive.

#### New Nissan Z Will Officially Debut September 15

The long wait for a new version of the Nissan Z is almost over. Nissan will officially show a prototype version of the sports car on September 15. That means the production Z35-generation car can't be too far off.
<br>
Nissan first teased the new Z a few months ago, showing its silhouette in a video alongside many other upcoming Nissan models. We expect it to be called 400Z and for it to be powered by a twin-turbocharged 3.0-liter V-6 engine producing around 400 horsepower. A manual transmission is a must in our view, although an automatic may be offered as well.

#### Mercedes Floods 2021 S-Class with New and Updated Technology

Mercedes-Benz calls this the first digital S-class and brings technology closer to the driver with features like a 3D head-up map display and headrest speakers.
<br>
The difference is apparent as soon as you sit in the 2021 Mercedes S-class. Gone are the landscape display and the center-console touchpad with its hand rest. In its place is an OLED 12.8-inch touchscreen that houses the latest edition of the automaker's MBUX infotainment system. Mercedes calls the vehicle "the first digital S-class." With 27 fewer hard buttons than the previous generation plus a new screen, a new MBUX layout, a 3D dash cluster, and a new processor, the 2021 S-class dives deeper into the world of tech.

### Expo

#### Suzuki Jimny Revealed

Maruti Suzuki wants to up its game in the SUV space and while the Futuro-e concept gives us a peek into what to expect, the company has also brought the Jimny to India at the 2020 Auto Expo. The model that has come to your shore is the bigger Suzuki Jimny Sierra, sold in Europe, instead of the shorter Kei car version of the SUV that is sold in Japan. The reigning 2019 World Urban Car of the Year may be rebadged Gypsy for India - since that model has had a cult following in urban and rural India. But the Jimny name has also been catapulted to stardom in India over the past few months.

#### Tata Sierra EV

The Tata Sierra was introduced in 1991 and is the first off-road Sport Utility vehicle produced by the Indian company; in reality the Sierra is the "closed" version of the Tata Telcoline pick-up originally launched in 1988 from which it takes all the mechanical parts, the front and the internal dashboard. The differences are in the shortened wheelbase at 2.40 meters (compared to the single-cab Telcoline). The Sierra was also one of the first cars for private transport in India and, being built on the Tata platform X2 with side members and crossbars, could be used on every road surface, especially the uneven ones being proposed both rear-wheel drive and four-wheel drive with reduced marches. Compared to the Telcoline, soundproofing has been improved, making the interior more comfortable.
