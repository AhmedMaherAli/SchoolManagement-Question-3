## Here are the 3 most critical issues

- The line: </div onclick="updateQty(@line.Id)"> combined with document.forms[0].submit();
    If a user clicks anywhere in that row—including clicking on the <input> box just to change a quantity—the entire form immediately POSTs 
    to the server and triggers a full page reload. If a parent wants to change the quantity from "1" to "12", 
    clicking the box submits the form before they can even type the "2". During the August back-to-school rush, 
    this generates massive amounts of unnecessary server traffic (effectively acting as a self-inflicted DDoS attack) and creates a deeply frustrating,
    broken user experience.

- Line: </input name="qty_@line.Id" value="@line.Quantity" />
    By naming the inputs dynamically (qty_14, qty_22), this page completely breaks ASP.NET Core's powerful built-in Model Binding. When the form is submitted, the        backend won't easily map this to a clean List<OrderLine> object.
