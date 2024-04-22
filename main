import java.util.Scanner;
public void main(String[] args){

    Scanner input = new Scanner(System.in);

    electronic phone = new electronic(1,"smartphone",599.9f,"Samsung",1);
    clothing clothing = new clothing(2,"T-shirt",19.99f,"Medium","Cotton");
    book book = new book(3,"OOP",39.99f,"O’Reilly","X Publications");

    System.out.println("Welcome to the E-commerce System!");
    System.out.println("Entre your ID");
    int id = input.nextInt();
    input.nextLine();
    System.out.println("name");
    String name = input.nextLine();
    System.out.println("address");
    String address = input.nextLine();
    customer customer = new customer(id,name,address);

    System.out.println("How many products do you want to add to your cart");
    int size = input.nextInt();
    cart cart = new cart(customer.getId(),size);
    for (int i = 0; i <size;i++) {
        System.out.println("Which product do you want to add? 1- Smartphone 2- T-shirt 3- OOP Book");
        int choice = input.nextInt();
        product product;
        switch(choice){
            case 1:
                product = new electronic(1, "Smartphone", 599.9f, "Samsung", 1);
                break;
            case 2:
                product = new clothing(2,"T-shirt",19.99f,"Medium","Cotton");
                break;
            case 3:
                product = new book(3,"OOP",39.99f,"O’Reilly","X Publications");
                break;
            default:
                System.out.println("Invalid choice, try again");
                i--;
                continue;
        }   cart.addProduct(product,i);
    }
    System.out.println("Your total is " + cart.calculate_price() + ". Would you like to confirm your order? 1- Yes 2- No");
    int choice = input.nextInt();
    if (choice ==1){
        System.out.println("order summary");
        order order;
        order = new order(id,1, cart.getProducts(), (float)cart.calculate_price());
        order.order_info();
    } else{
        System.out.println("come back soon !");
    }
}
class product{
    private int id;
    private String name;
    private float price;
    product(int id , String name , float price){
        this.id = Math.abs(id);
        this.name = name;
        this.price = Math.abs(price);
    }
    void setId(int id){
        this.id = Math.abs(id);
    }
    void setName(String name){
        this.name = name;
    }
    void setPrice(float price){
        this.price = Math.abs(price);
    }
    int getId(){
        return id;
    }
    String getName(){
        return name;
    }
    float getPrice(){
        return price;
    }

}
class electronic extends product{
    String brand;
    int warranty;
    electronic(int id, String name, float price , String brand , int warranty) {
        super(id, name, price);
        this.brand = brand;
        this.warranty = Math.abs(warranty);
    }
    void setBrand(String brand){
        this.brand = brand;
    }
    void setWarranty(int warranty){
        this.warranty = Math.abs(warranty);
    }
    String getBrand(){
        return brand;
    }
    int getWarranty(){
        return warranty;
    }
}
class clothing extends product{
    String size;
    String fabric;

    public clothing(int id, String name, float price, String size, String fabric) {
        super(id, name, price);
        this.size = size;
        this.fabric = fabric;
    }

    public void setSize(String size) {
        this.size = size;
    }

    public void setFabric(String fabric) {
        this.fabric = fabric;
    }

    public String getSize() {
        return size;
    }

    public String getFabric() {
        return fabric;
    }
}
class book extends product{
    String author;
    String publisher;

    public book(int id, String name, float price, String author, String publisher) {
        super(id, name, price);
        this.author = author;
        this.publisher = publisher;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public void setPublisher(String publisher) {
        this.publisher = publisher;
    }

    public String getAuthor() {
        return author;
    }

    public String getPublisher() {
        return publisher;
    }

}
class customer{
    int id;
    String name;
    String address;
    customer(int id , String name , String address){
        if(id > 0){
            this.id = id;
        }else{
            this.id = -1 * id;
        }
        this.name = name;
        this.address = address;
    }

    public void setId(int id) {
        this.id = id;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setAddress(String address) {
        this.address = address;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getAddress() {
        return address;
    }
}
class cart{
    int customerId;
    int nproducts;
    product []products;
    boolean []active_prod;
    int c = 0;

    public cart(int customerId, int nproducts) {
        this.customerId = customerId;
        this.nproducts = nproducts;
        products = new product[nproducts];
        active_prod = new boolean[nproducts];
    }

    public void setCustomerId(int customerId) {
        this.customerId = customerId;
    }

    public void setNproducts(int nproducts) {
        this.nproducts = nproducts;
    }

    public int getCustomerId() {
        return customerId;
    }

    public int getNproducts() {
        return nproducts;
    }

    public product[] getProducts() {
        return products;
    }

    public void addProduct(product product , int val){
        if (val >= 0 && val < nproducts) {
            products[val] = product;
        } else {
            System.out.println("incorrect size");
        }
    }
    public void removeProduct(int a){
        active_prod[a] = false;
    }
    public float calculate_price(){
        float sum=0;
        for (int i=0;i <nproducts;i++) {
            if (products[i] != null) {
                sum += products[i].getPrice();
            }
        }
        //System.out.println("the total is" + sum);
        return sum;
    }
    public boolean check_max(){
        return c<nproducts;
    }
}
class order{
    int customerId;
    int orderId;
    product []products;
    float totalPrice;
    //int nproducts;

    public order(int customerId, int orderId, product[] products , float totalPrice ) {
        this.customerId = Math.abs(customerId);
        this.orderId = Math.abs(orderId);
        this.products = products;
        this.totalPrice = Math.abs(totalPrice);
        //this.nproducts = nproducts;
    }
    public void order_info(){
        //int sum = 0;
        System.out.println("order id : "+orderId);
        System.out.println("customer id : "+customerId);
        System.out.println("products : ");
        for(int i = 0; i<products.length ; i++){
            System.out.println(products[i].getName() + " : " + products[i].getPrice());
            //sum+=products[i].getPrice();
        }
        System.out.println("total price : "+totalPrice);
    }
}
