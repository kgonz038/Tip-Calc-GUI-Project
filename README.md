# Tip-Calc-GUI-Project

**Summary:** 
This project was my first attempt at Java GUI, or Graphical User Interface, and learning how to add buttons, drop down events and more user interactions.
This application simulates a tip calculator based on 20% percent. This is done by utilizing text fields, labels, actions, scenes and event handlers.


<img src="java tip calc gui fx project.gif">

## [Java File](https://github.com/kgonz038/Tip-Calc-GUI-Project/blob/main/TipCalculatorGUI_kimberly_gonzalez.java)


```java


/**
 * This application simulates a tip calculator for the Laguna Madre restaurant
 * based on 20% percent. 
 * 
 * @author kgonz038
 */
public class TipCalculatorGUI_kimberly_gonzalez extends Application 
{
    //Fields for the total restaurant charge and the total tip
    private TextField totalCharge;
    private Label tipTotal;
    
    /**
     * Main method calls the launch method
     * 
     * @param args the command line arguments
     */
    public static void main(String[] args) 
    {
        launch(args);
    }
    
    /**
     * This start method contains the controls and containers used for the tip
     * calculator. 
     * 
     * @param primaryStage 
     */
    @Override
    public void start(Stage primaryStage) 
    {
        //Sets the stage title name as tip calculator
        primaryStage.setTitle("Tip Calculator");

        //Creates a label with a String passed as an argument
        Label total = new Label("Total Restaurant Charge:");

        //Creates another label with a String argument
        Label toTip = new Label("Amount to Tip:");
   
        //Creates a text field that will retrieve the text entered
        totalCharge = new TextField();
        
        //Creates an empty label to used after the text field
        tipTotal = new Label();
        
        //Creates a Button to perform the calculation for the 20% tip
        Button calcTipButton = new Button("Calculate Tip");

        //Register the event handler for clicking the button
        calcTipButton.setOnAction(new TipCalcButtonHandler());
        
        //Creates an Image object that will be retrieved from a online logo link
        Image image = new Image("https://tinyurl.com/y8z3hmpx");
        
        //Creates an ImageView object that will display the restaurant logo image
        ImageView imageView = new ImageView(image);
        
        //Adds the labels, text field, image logo and button into the vertical box conatiner
        VBox vbox = new VBox(10, imageView, total, totalCharge, calcTipButton, toTip, tipTotal);
        
        //Sets the vertical box to a center alignment 
        vbox.setAlignment(Pos.CENTER);
        
        //Sets the vertical box padding to 10 pixels
        vbox.setPadding(new Insets(10));

        //Creates a Scene that adds within the root nodes the vertical box
        Scene Scene1 = new Scene(vbox);
        
        //Applies the CSS style sheet to this JavaFx application
        Scene1.getStylesheets().add("tipcalculatorgui_kimberly_gonzalez/TipGUIStyle_kimberly_gonzalez.css");

        //Adds the scene to the stage
        primaryStage.setScene(Scene1);

        //Displays the window
        primaryStage.show();
    }
    
    /**
     * This implements the EventHandler interface, which then execute the method
     * that will calculate the 20% tip based on the user's total restaurant 
     * charge. It then displays that total tip percentage with the empty label 
     * created beforehand. 
     */
    class TipCalcButtonHandler implements EventHandler<ActionEvent>
   {
      @Override
      public void handle(ActionEvent event)
      {
         //The text field grabs the total charge entered
         Double charge = Double.parseDouble(totalCharge.getText());
         
         //Calculates the total tip and assigns it to tipCalcTotal
         Double tipCalcTotal = charge * 0.20;
         
         //The calculation of the tip is then set to the empty label
         tipTotal.setText(String.format("$%.2f", tipCalcTotal));
      }
    }    
}
```
