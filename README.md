- 👋 Hi, I’m @OlidaHirma
-fun main() {

    print("Enter a number: ")
    val num = readLine()!!.toDouble()

    val result = convertToWords(num)
    println("Number in words: $result")
}

fun convertToWords(n: Double): String {
    val firstTwenty = arrayOf(
        "", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine",
        "Ten", "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen"
    )

    val tens = arrayOf(
        "", "", "Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety"
    )
    val newN = n.toInt()

    return when {
        n < 20.0 -> firstTwenty[newN]
        n < 100.0 -> "${tens[(newN / 10.0).toInt()]}${if (n % 10.0 != 0.0) " ${firstTwenty[(n % 10.0).toInt()]}" else ""}"
        n < 1000.0 -> "${firstTwenty[(n / 100.0).toInt()]} Hundred${if (n % 100.0 != 0.0) " and ${convertToWords(n % 100.0)}" else ""}"
        n < 100000000.0 -> "${convertToWords(n / 1000)} Thousand${if (n % 1000 != 0.0) " ${convertToWords(n % 1000.0)}" else ""}"
        else -> "${convertToWords(n / 1000000.0)} Million${if ((n % 1000000).toInt() != 0) " ${convertToWords(n % 1000000)}" else ""}"
    }
} 

