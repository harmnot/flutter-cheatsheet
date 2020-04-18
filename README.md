# FLUTTER DOC

##### create fluuter

```bash
 flutter create --org com.name-of-project-or-what-ever name-of-project
```

#### How to Loop in  Flutter 

```dart
ListView.builder() {
	itemBuilder: (ctx, index) {
		// return Card? Column?
		return Card(
			child: // .... do something here
		)
	},
  itemCount: // length of data want to loop E.g array.length
}
```

#### make DateTime type to String [int package](https://pub.dev/packages/intl)

```dart
import 'package:intl/intl.dart';

DateFormat.yMMMD().format("DATE_HERE") 
//May 19, 2020 
```

#### create Form

```dart
final stateForTitle = TextEditingController()
  
final stateForBody = TextEditingController()
  
// usage 
TextFormFiled(
	controller: stateForTitle,
  decoration: InputDecoration(
                labelText: "Title"
             ),
)
```

#### how to make validate in form 

```dart
final _formKey = GlobalKey<FormState>();

// usage
Form(
  key: _formKey
)

TextFormFiled(
  keyboardType: TextInputType.numberWithOptions(decimal: true), // for strict data type
  validator: (value) {
    return value.isEmpty ? "Required field" : null;
  }
)
  
// before we click; that _formKey work like this on button
FlatButton(
	onPressed: () {
    if(_formKey.currentState.validate()) {
      // do something if the field not empty or whatever you want to validate in validator
    }
    // if condition wrong, the "Required field" will be showing on below input form
  }
)
```

####  Space around Column widget

```dart
 SizedBox(height: 10),

// if you want responsive use LayoutBuilder 
LayoutBuilder(builder: (ctx, constrains){
  Column: Widget<> [
    Text("Some Text Here"),
    SizedBox(height: constrains.maxHeight * 0.05)
  ]
})
```

#### Model with required field

```dart
import 'package:flutter/foundation.dart';

class Transaction {
  final String id;
  final String title;
  final double amount;
  final DateTime date;

  Transaction({
    @required this.id,
    @required this.title,
    @required this.amount,
    @required this.date
  });
}
```

#### Data type

```dart
List<Map<String, Object>> // [ {name: "heheh"}]
List<Car> // [ { name: "toyota"}]
String
double
DateTime  
```

#### Make Circle with Container widget

```dart
Container(
	decoration: BoxDecoration(
            	color: Colors.amber,
              shape: BoxShape.circle
          	),
  width: "NUMBER",
  height: "NUMBER",
)
```



### Modal / Pop up

#### Show Date Picker 

```dart
// promise
void _presentDatePickerModal() {
  showDatePicker(
      context: context,
      initialDate: DateTime.now(),
      firstDate: DateTime(2019),
      lastDate: DateTime.now(),
  ).then((pickedDateByUser) {
    // do something here
  })
}
```



#### Show Modal

```dart
showModalBottomSheet(
  context: ctx,
  builder: (_) => GestureDetector(
    onTap: () {},
    child: // your widget form or what ever here,
    behavior: HitTestBehavior.opaque,
  )
);

// close the modal when u click the submit NOTE: call this on your methods
Navigator.of(context).pop();
```

#### Modal size Error

```dart
// if your modal covered by keyboard, wrap your modal / form with this widget below
SingleChildScrollView()
```



### Responsive



#### MediaQuery for responsive 

```dart
Container(
  height: (MediaQuery.of(context).size.height - appBar.preferredsize.height() -MediaQuery.of(context).padding.top) * "NUMBER_YOU_WANT",
)
  
// text scale
final curScaleFactor = MediaQuery.of(context).textScaleFactor; 

Text('This changes!', style: TextStyle(fontSize: 20 * curScaleFactor));

// this builder is to gets parent size
LayoutBuilder(builder: (ctx, constrains){
  Container(
    height: constrains.maxHeight * 0.7, // 7%
    width: 10,
    child: // child widgets here
  )
})
```

#### Get Orientation Landscape or Potrait

```dart
final isLandscape = MediaQuery.of(context).orientation == Orientation.landscape;
```



### Navigation / Routing 

#### Routing push to another widget

```dart
Navigator.of(context).push(
   MaterialPageRoute(
      builder: (_) => nameWidgetForThisRoute(propHere: "text_here")
   )
);

Navigator.pushNamed(context, ‘/routingName’);

Navigator.pushReplaceNames(context, “/nameRoute”, arguments : payload);
```

