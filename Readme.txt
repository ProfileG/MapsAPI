//Simple project in console application...

[STAThread()]
static void Main( string[] args )
{
PointD[][] DotsArray = new PointD[][]
{
new PointD[] { new PointD(76.889332, 43.238630), new PointD(76.947697, 43.242520) },
new PointD[] { new PointD(76.886585, 43.259083), new PointD(76.949757, 43.228337) },
new PointD[] { new PointD(76.744028, 43.227022), new PointD(76.885493, 43.272172) },
new PointD[] { new PointD(76.905406, 43.201009), new PointD(76.948149, 43.242437) },
new PointD[] { new PointD(76.986945, 43.284965), new PointD(76.887724, 43.224739) },
new PointD[] { new PointD(76.938536, 43.353955), new PointD(77.054408, 43.302073) },
new PointD[] { new PointD(76.765501, 43.358840), new PointD(76.827128, 43.285146) },
new PointD[] { new PointD(76.960693, 43.271698), new PointD(77.128407, 43.306433) },
new PointD[] { new PointD(77.025238, 43.319846), new PointD(77.225567, 43.388616) },
new PointD[] { new PointD(76.994167, 43.497559), new PointD(77.169864, 43.399362) }
};

foreach (PointD[] Dots in DotsArray)
{
Thread thread = new Thread(TestThread);
thread.SetApartmentState(ApartmentState.STA);
thread.Start(Dots);
}

Console.WriteLine("END");
Console.ReadLine();
}

public static void TestThread(object Dots)
{
Route route = new Route(10);
route = route.Load(Dots as PointD[]); 
if (route != null)
{
string RouteLength = route.RouteLength; // Длина в метрах
string RouteJamsTime = route.RouteJamsTime; // Время проезда в секундах с учетом пробок
string RouteTime = route.RouteTime; // Время проезда в секундах
string RouteHumanLength = route.RouteHumanLength; // Возвращает строковое представление длины маршрута с единицами измерения.
string RouteHumanJamsTime = route.RouteHumanJamsTime; // Возвращает строковое представление времени проезда маршрута с единицами измерения с учетом пробок.
string RouteHumanTime = route.RouteHumanTime; // Возвращает строковое представление времени проезда маршрута с единицами измерения.

Console.WriteLine("---------------------------");
Console.WriteLine(RouteLength);
Console.WriteLine(RouteJamsTime);
Console.WriteLine(RouteTime);
Console.WriteLine(RouteHumanLength);
Console.WriteLine(RouteHumanJamsTime);
Console.WriteLine(RouteHumanTime);
Console.WriteLine("---------------------------");
}
}