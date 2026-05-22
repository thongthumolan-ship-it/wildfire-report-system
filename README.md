from fastapi import FastAPI

app = FastAPI()

fire_reports = []

@app.get("/")
def home():
    return {"message": "Wildfire API Running"}

@app.get("/reports")
def get_reports():
    return fire_reports

@app.post("/report")
def create_report(report: dict):
    fire_reports.append(report)
    return {
        "status": "success",
        "data": report
    }
