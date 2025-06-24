#Name: Duraan-salad-mohamed-
// Id:C6230034 
import java.util.Scanner;

public class EVCPlusApp {
    // Scanner-ka user input-ka
    static Scanner scanner = new Scanner(System.in);

    // Haraaga (balance) ee account-ka
    static double balance = 100.0;

    // PIN code ee xaqiijinta wareejinta lacagta
    static String pinCode = "1234";

    // Array-ga shirkadaha biilka (bill payment companies)
    static String[] companies = {"Electricity", "Water", "Internet", "TV"};

    // Array-ga MIFI packages iyo qiimaha
    static String[] mifiPackages = {"Daily - $1", "Weekly - $5", "Monthly - $15"};

    public static void main(String[] args) {
        mainMenu();
    }

    /**
     * Menu-ga ugu weyn ee adeegyada EVCPlus
     */
    public static void mainMenu() {
        int choice;
        do {
            System.out.println("\nEVCPlus");
            System.out.println("1. Itus Haraaga");
            System.out.println("2. Kaarka hadalka");
            System.out.println("3. Bixi Biil");
            System.out.println("4. U wareeji EVCPlus");
            System.out.println("5. Warbixin Kooban");
            System.out.println("6. Salaam Bank");
            System.out.println("7. Kordhi Xisaabtaada");
            System.out.println("8. Maareynta");
            System.out.println("9. Bill Payment");
            System.out.println("0. Exit");
            System.out.print("Dooro adeeg: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1 -> showBalance();
                case 2 -> kaarkaHadalkaMenu();
                case 3 -> bixiBiil();
                case 4 -> uWareeji();
                case 5 -> warbixinKooban();
                case 6 -> salaamBank();
                case 7 -> kordhiXisaabta();
                case 8 -> maareynta();
                case 9 -> billPayment();
                case 0 -> System.out.println("Mahadsanid.");
                default -> System.out.println("Fadlan dooro lambarka saxda ah.");
            }
        } while (choice != 0);
    }

    /**
     * Tus haraaga account-ka
     */
    public static void showBalance() {
        System.out.println("Haraagaagu waa: $" + balance);
    }

    /**
     * Menu kaarka hadalka oo ka kooban 4 adeeg (method-ka weyn)
     */
    public static void kaarkaHadalkaMenu() {
        System.out.println("Kaarka hadalka:");
        System.out.println("1. Ku Shubo Airtime");
        System.out.println("2. Ugu Shub Airtime");
        System.out.println("3. MIFI Packages");
        System.out.println("4. Ku shubo Internet");
        System.out.print("Dooro: ");
        int option = scanner.nextInt();

        switch (option) {
            case 1 -> kuShuboAirtime();
            case 2 -> uguShubAirtime();
            case 3 -> showMifiPackages();
            case 4 -> kuShuboInternet();
            default -> System.out.println("Doorasho khaldan.");
        }
    }

    /**
     * Method-ka ku shubista Airtime
     */
    public static void kuShuboAirtime() {
        System.out.print("Geli qadarka Airtime-ka la rabo in lagu shubo: ");
        double amount = scanner.nextDouble();
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Waa lagu shubay Airtime $" + amount);
        } else {
            System.out.println("Haraagaaga kuma filna.");
        }
    }

    /**
     * Method-ka ugu shubista Airtime qof kale
     */
    public static void uguShubAirtime() {
        System.out.print("Geli numberka aad ugu shubeyso Airtime: ");
        String number = scanner.next();
        System.out.print("Geli qadarka Airtime-ka: ");
        double amount = scanner.nextDouble();
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Waad ugu shubtay " + number + " Airtime $" + amount);
        } else {
            System.out.println("Haraagaaga kuma filna.");
        }
    }

    /**
     * Tus MIFI packages oo ku jira array
     */
    public static void showMifiPackages() {
        System.out.println("MIFI Packages:");
        for (String pkg : mifiPackages) {
            System.out.println("- " + pkg);
        }
    }

    /**
     * Ku shubo Internet
     */
    public static void kuShuboInternet() {
        System.out.print("Geli qadarka Internet-ka la rabo in lagu shubo: ");
        double amount = scanner.nextDouble();
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Internet ayaa lagu shubay $" + amount);
        } else {
            System.out.println("Haraagaaga kuma filna.");
        }
    }

    /**
     * Bixi biil oo magac iyo lacag geliya
     * Shirkadaha biilka ayaa laga yaabaa in la ballaariyo array-da companies
     */
    public static void bixiBiil() {
        System.out.println("Shirkadaha biilka:");
        for (int i = 0; i < companies.length; i++) {
            System.out.println((i + 1) + ". " + companies[i]);
        }
        System.out.print("Dooro shirkadda biilka: ");
        int choice = scanner.nextInt();

        if (choice >= 1 && choice <= companies.length) {
            String billName = companies[choice - 1];
            System.out.print("Geli qadarka biilka " + billName + ": ");
            double amount = scanner.nextDouble();
            if (amount <= balance) {
                balance -= amount;
                System.out.println("Waad bixisay biilka " + billName + " oo ah $" + amount);
            } else {
                System.out.println("Haraagaaga kuma filna.");
            }
        } else {
            System.out.println("Doorasho khaldan.");
        }
    }

    /**
     * U wareeji lacag qof kale
     * PIN ayaa lagu xaqiijiyaa halkan
     */
    public static void uWareeji() {
        System.out.print("Geli numberka aad u wareejinayso: ");
        String number = scanner.next();
        System.out.print("Geli qadarka lacagta la wareejinayo: ");
        double amount = scanner.nextDouble();
        if (amount <= balance) {
            System.out.print("Geli PIN: ");
            String pin = scanner.next();
            if (pin.equals(pinCode)) {
                balance -= amount;
                System.out.println("Waad u wareejisay $" + amount + " numberka " + number);
            } else {
                System.out.println("PIN khaldan.");
            }
        } else {
            System.out.println("Haraagaaga kuma filna.");
        }
    }

    /**
     * Warbixin kooban oo ku saabsan haraaga
     */
    public static void warbixinKooban() {
        System.out.println("Warbixin: Haraaga hadda = $" + balance);
    }

    /**
     * Salaam Bank (waxqabadka waa placeholder)
     */
    public static void salaamBank() {
        System.out.println("Salaam Bank: Isku xidhid, Wareejin, Bank Info");
    }

    /**
     * Kordhi haraaga (Add money)
     */
    public static void kordhiXisaabta() {
        System.out.print("Geli qadarka aad rabto inaad ku shubto: ");
        double amount = scanner.nextDouble();
        balance += amount;
        System.out.println("Waad ku shubtay $" + amount);
    }

    /**
     * Maareynta - Badal PIN
     */
    public static void maareynta() {
        System.out.println("1. Badal PIN");
        System.out.print("Dooro: ");
        int choice = scanner.nextInt();
        if (choice == 1) {
            System.out.print("Geli PIN cusub: ");
            pinCode = scanner.next();
            System.out.println("PIN waa la beddelay.");
        }
    }

    /**
     * Bill Payment oo leh array shirkado hore loo qeexay
     * (Isticmaal array-ga companies)
     */
    public static void billPayment() {
        System.out.println("Shirkadaha biilka:");
        for (int i = 0; i < companies.length; i++) {
            System.out.println((i + 1) + ". " + companies[i]);
        }
        System.out.print("Dooro shirkadda: ");
        int choice = scanner.nextInt();

        if (choice >= 1 && choice <= companies.length) {
            String company = companies[choice - 1];
            System.out.print("Geli qadarka biilka shirkadda " + company + ": ");
            double amount = scanner.nextDouble();
            if (amount <= balance) {
                balance -= amount;
                System.out.println("Waad bixisay bill-ka " + company + " ee ah $" + amount);
            } else {
                System.out.println("Haraagaaga kuma filna.");
            }
        } else {
            System.out.println("Doorasho khaldan.");
        }
    }
}
