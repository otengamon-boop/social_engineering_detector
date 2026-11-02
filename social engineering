
import re

# Social engineering warning signs
warning_signs = {
    "Urgency": [
        "immediately",
        "urgent",
        "act now",
        "within 24 hours",
        "right now"
    ],

    "Threats": [
        "account blocked",
        "account suspended",
        "legal action",
        "permanently closed"
    ],

    "Password requests": [
        "send your password",
        "share your password",
        "confirm your password",
        "provide your login details"
    ],

    "Financial manipulation": [
        "transfer money",
        "send money",
        "bank details",
        "payment required"
    ],

    "Prize scams": [
        "you have won",
        "claim your prize",
        "free gift",
        "claim reward"
    ],

    "Suspicious links": [
        "click here",
        "verify your account",
        "login here",
        "update your details"
    ]
}


def analyse_message(message):

    score = 0
    detected = []

    message_lower = message.lower()

    # Search for warning signs
    for category, phrases in warning_signs.items():

        matches = []

        for phrase in phrases:
            if phrase in message_lower:
                matches.append(phrase)

        if matches:
            score += len(matches)
            detected.append((category, matches))

    # Detect URLs for further caution
    urls = re.findall(
        r"https?://\S+|www\.\S+",
        message_lower
    )

    if urls:
        score += 1
        detected.append(
            ("Links found", urls)
        )

    # Determine risk level
    if score >= 4:
        risk = "HIGH RISK"
    elif score >= 2:
        risk = "MEDIUM RISK"
    else:
        risk = "LOW RISK"

    return risk, detected


def main():

    print("=" * 50)
    print("       SOCIAL ENGINEERING DETECTOR")
    print("=" * 50)

    print("Analyse a suspicious message below.")
    print("Do not enter real passwords or private details.")

    message = input("\nEnter message: ")

    risk, detected = analyse_message(message)

    print("\n" + "=" * 50)
    print("ANALYSIS RESULTS")
    print("=" * 50)

    print("Risk Level:", risk)

    if detected:
        print("\nWarning signs detected:")

        for category, matches in detected:
            print("\nCategory:", category)
            print("Indicators:", ", ".join(matches))

    else:
        print("\nNo listed warning signs were detected.")

    print("\nSECURITY RECOMMENDATIONS")
    print("- Do not share passwords or OTP codes.")
    print("- Verify unexpected requests independently.")
    print("- Avoid clicking suspicious links.")
    print("- Contact the organisation using official channels.")
    print("- Report suspicious messages.")

    print("\nNote: This is an educational detection tool.")
    print("It cannot guarantee that a message is safe.")


if __name__ == "__main__":
    main()
