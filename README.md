
## Examples
```html
<!DOCTYPE html>

<html lang="en" xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="utf-8" />
    <title></title>
</head>
<body>
    <div class="shop">

        <strong>Online shopping</strong>
        <a href="www.shop.com">Homepage</a>

        <div class="all-productions">

            <div class="production">
                <strong>Galaxy S9</strong>
                <img class="thumb" src="https://cdn.tgdd.vn/Products/Images/42/177047/samsung-galaxy-s9-tim-1-400x460.png" />
                Tag
                <p class="tag">
                    <span>Phone</span>
                    <span>Galaxy</span>
                    <span>Smartphone</span>
                </p><br />
                    <table class="specs">
                        <tr>
                            <td>
                                NETWORK
                            </td>
                            <td class="network">
                                GSM / HSPA / LTE
                            </td>
                        </tr>
                        <tr>
                            <td>
                                Resolution
                            </td>
                            <td class="resolution">
                                1125 x 2436 pixels, 19.5:9 ratio (~458 ppi density)
                            </td>
                        </tr>
                        <tr>
                            <td>
                                OS
                            </td>
                            <td class="resolution">
                                iOS 11.1.1, upgradable to iOS 11.4.1
                            </td>
                        </tr>
                    </table>
                Manufacture <a href="samsung.com">Samsung</a>
            </div>

            <div class="production">
                <strong>iPhone X</strong>
                <img class="thumb" src="https://cdn.tgdd.vn/Products/Images/42/172602/iphone-x-64gb-silver-400x460.png" />
                Tag
                <p class="tag">
                    <span>Phone</span>
                    <span>iPhone</span>
                    <span>Smartphone</span>
                </p><br />
                <table class="specs">
                    <tr>
                        <td>
                            NETWORK
                        </td>
                        <td class="network">
                            GSM / CDMA / HSPA / EVDO / LTE
                        </td>
                    </tr>
                    <tr>
                        <td>
                            Resolution
                        </td>
                        <td class="resolution">
                            1440 x 2960 pixels, 18.5:9 ratio (~529 ppi density)
                        </td>
                    </tr>
                    <tr>
                        <td>
                            OS
                        </td>
                        <td class="resolution">
                            Android 8.0 (Oreo)
                        </td>
                    </tr>
                </table>
                Manufacture <a href="apple.com">Apple</a>
            </div>
        </div>
    </div>
</body>
</html>

```

```c#
// Define classes

    class Manufactory
    {
        [MapToHref("")]
        public string Url { get; set; }

        [MapToText("")]
        public string Name { get; set; }
    }

    class Specification
    {
        [MapToText(".network")]
        public string Network { get; set; }

        [MapToText(".resolution")]
        public string Resolution { get; set; }

        [MapToText(".resolution")]
        public string Os { get; set; }
    }

    class Production
    {
        [MapToText("strong")]
        public string Title { get; set; }

        [MapToAttr(".thumb", "src")]
        public string ThumbUrl { get; set; }

        [MapToText(".tag span")]
        public string[] Tags { get; set; }

        [MapTo(".specs")]
        public Specification Specification { get; set; }

        [MapTo("a")]
        public Manufactory Manufactory { get; set; }
    }

    class Shop
    {
        [MapToText("strong")]
        public string Title { get; set; }

        [MapToHref("a")]
        public string Url { get; set; }

        [MapTo(".all-productions .production")]
        public Production[] Productions { get; set; }
    }

var htmlDocument =  new HtmlDocument();
htmlDocument.LoadHtml(htmlContent);

var shop = new Shop();
htmlDocument.DocumentNode.Bind(shop);
```
