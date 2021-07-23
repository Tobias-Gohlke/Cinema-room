fun creatCine (cine: Array<Array<String>>, seats: Int, rows: Int) :Array<Array<String>> {
    for (i in 0..rows) {
        for (j in 0..seats) {
            if (i == 0) {
                if (j == 0) {
                    cine[i][j] = " "
                } else {
                    cine[i][j] = "${j}"
                }
            } else {
                if (j == 0) {
                    cine[i][j] = "$i"
                } else {
                    cine[i][j] = "S"
                }
            }
        }
    }
    return cine
}

fun printCine(cine: Array<Array<String>>, seats: Int, rows: Int) {
    println("\nCinema:")
    for (i in 0..rows) {
        for (j in 0..seats) {
            print("${cine[i][j]} ")
        }
        println()
    }
}

fun changeCine(cine: Array<Array<String>>, rowNumber: Int, seatsNumber: Int):Array<Array<String>>  {
    cine[rowNumber][seatsNumber] = "B"
    return cine
}

fun berTicket(row: Int, seats: Int, rowNumber: Int):Int {
    var dollar: Int
    if (row * seats <= 60) {
        dollar = 10
    } else {
        if (row % 2 != 0) {
            if (rowNumber <= row / 2) {
                dollar = 10
            } else dollar = 8
        } else {
            if (rowNumber <= row / 2) {
                dollar = 10
            } else dollar = 8
        }
    }
    return dollar
}

fun ticketprice(row: Int, seats: Int, rowNumber: Int, seatsNumber: Int, cine: Array<Array<String>>):Array<Array<String>> {
    val dollar = berTicket(row, seats, rowNumber)
    println("\nTicket price: $$dollar")

    return changeCine(cine, rowNumber, seatsNumber)
}

fun buyTicket(rows: Int, seats: Int, cine: Array<Array<String>>):Array<Array<String>> {
    var cine = cine
    var rowNumber: Int
    var seatsNumber: Int

    do {
        println("\nEnter a row number:")
        rowNumber = readLine()!!.toInt()
        println("Enter a seat number in that row:")
        seatsNumber = readLine()!!.toInt()

        if (rowNumber > rows || seatsNumber > seats) {
            println("\nWrong input!")
        } else if (cine[rowNumber][seatsNumber] == "B") {
            println("\nThat ticket has already been purchased!")
        }
    } while ( try { cine[rowNumber][seatsNumber] == "B" || rowNumber > rows && seatsNumber > seats } catch (e: ArrayIndexOutOfBoundsException) { true })
        cine = ticketprice(rows, seats, rowNumber, seatsNumber, cine)
    return cine
}

fun statistic(seats: Int, rows: Int, cine: Array<Array<String>>) {
    var numberTickets = 0
    var currentIncome = 0
    var totalIncome = 0

    for (i in 1..rows) {
        for (j in 1..seats) {
            if (cine[i][j] == "B") {
                numberTickets++
                currentIncome += berTicket(rows, seats, i)
            }
        }
    }

    var percentage ="%.2f".format((numberTickets.toDouble() / (rows.toDouble() * seats.toDouble())) * 100)

    for (i in 1..rows) {
        for (j in 1..seats) {
            totalIncome += berTicket(rows, seats, i)
        }
    }

    println("\nNumber of purchased tickets: $numberTickets")
    println("Percentage: $percentage%")
    println("Current income: $$currentIncome")
    println("Total income: $$totalIncome")
}

fun main() {

    println("Enter the number of rows:")
    var rows = readLine()!!.toInt()
    println("Enter the number of seats in each row:")
    var seats = readLine()!!.toInt()

    var cine = Array(rows + 1) {Array(seats + 1) { "" } }
    var cinema = creatCine(cine, seats, rows)

    while (true) {
        println("\n1. Show the seats")
        println("2. Buy a ticket")
        println("3. Statistics")
        println("0. Exit")
        var controli = readLine()!!.toInt()
        when (controli) {
            1 -> { printCine(cinema, seats, rows) }
            2 -> { cinema = buyTicket(rows, seats, cinema) }
            3 -> { statistic(rows, seats, cinema) }
            0 -> {break}
        }
    }
}
