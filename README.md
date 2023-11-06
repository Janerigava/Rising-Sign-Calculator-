# Rising-Sign-Calculator-
git init
git add .
git commit -m "Initial commit"
git remote add origin <repository_urlhttps://github.com/Janerigava/Rising-Sign-Calculator-/edit/main/README.md>
git push -u origin masterimport swisseph.*;

public class AstrologyCalculator {
    public static void main(String[] args) {
        SwissEph swissEph = new SwissEph();
        int iflag = SweConst.SEFLG_SPEED;

        // Set the birth details (date, time, and location)
        double birthDate = 1990.0; // Example: 1990-01-01
        double birthTime = 12.0;   // Example: 12:00 PM
        double latitude = 40.0;    // Example: 40 degrees North
        double longitude = 74.0;   // Example: 74 degrees West

        // Calculate the rising sign
        SwissLib planetaryPosition = new SwissLib();
        int[] houseCusps = new int[13];
        double[] ascendant = new double[2];

        swissEph.swe_houses(birthDate, iflag, latitude, longitude, houseCusps, ascendant);

        int risingSign = (int) Math.floor(ascendant[0] / 30.0) + 1;

        // Determine the name of the rising sign
        String[] zodiacSigns = {
            "Aries", "Taurus", "Gemini", "Cancer", "Leo", "Virgo", "Libra",
            "Scorpio", "Sagittarius", "Capricorn", "Aquarius", "Pisces"
        };

        String risingSignName = zodiacSigns[risingSign - 1];

        System.out.println("The rising sign is: " + risingSignName);
    }
}

