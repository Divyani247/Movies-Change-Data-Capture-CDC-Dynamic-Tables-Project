# Movies-Change-Data-Capture-CDC-Dynamic-Tables-Project
## Overview

This project demonstrates a comprehensive **Change Data Capture (CDC)** solution using Snowflake's advanced features including **Streams**, **Tasks**, and **Dynamic Tables**. The system provides real-time movie booking analytics with enhanced derived fields, automated data processing, and an interactive Streamlit dashboard.

## Architecture

### Core Components

1. **Source Table**: `raw_movie_bookings` - Stores raw booking transactions with timestamps
2. **Stream**: `movie_bookings_stream` - Captures all changes to source table
3. **CDC Events Table**: `movie_booking_cdc_events` - Stores raw stream data with metadata
4. **Dynamic Tables**: 
   - `movie_bookings_filtered` - Enhanced view with derived fields and business logic
   - `movie_booking_insights` - Comprehensive analytics with business categorizations
5. **Tasks**: Automated processing of CDC events (every 1 minute)
6. **Streamlit Dashboard**: Clean, beginner-friendly analytics interface

### Enhanced Data Flow

```
Raw Bookings → Stream → CDC Events → Enhanced Filtered Table → Analytics Dashboard
     ↓              ↓         ↓              ↓                    ↓
  INSERT/      Captures   Raw Stream    Derived Fields        Interactive
 UPDATE/       Changes    Data +        + Business Logic      Visualization
DELETE                     Metadata     + Data Quality
```

### Key Enhancements

- **Derived Fields**: Business categorizations (ACTIVE/INACTIVE, SINGLE/GROUP, BUDGET/PREMIUM)
- **Data Quality**: Built-in validation and quality scoring
- **Enhanced Analytics**: Rich metrics with business context
- **Simplified Dashboard**: Clean interface focused on essential features

## 📊 Key Features

### Real-time CDC Processing
- **Automatic Change Detection**: Streams capture all INSERT, UPDATE, DELETE operations
- **Raw Stream Data**: Complete change history with metadata
- **Near Real-time Processing**: Tasks run every minute, dynamic tables refresh every 2 minutes
- **Timestamp Tracking**: Automatic created_at and updated_at management

### Enhanced Analytics with Derived Fields
- **Business Categorizations**: 
  - Status Categories: ACTIVE (BOOKED) vs INACTIVE (CANCELLED)
  - Size Categories: SINGLE, GROUP, LARGE_GROUP based on ticket count
  - Price Categories: BUDGET, STANDARD, PREMIUM based on ticket price
- **Revenue Analysis**: Active revenue vs lost revenue tracking
- **Data Quality Metrics**: Built-in validation and quality scoring
- **Time-based Analysis**: Booking hour, day of week patterns

### Simplified Dashboard
- **Essential Filters**: Date range, booking status, movie selection
- **Key Metrics**: Total bookings, revenue, active/lost revenue
- **Core Visualizations**: Revenue by status, booking distribution, movie performance
- **Clean Interface**: Beginner-friendly design with focused functionality
- **Export Capabilities**: Download filtered data as CSV

### Sample Data

The project includes realistic sample data with:
- **5 initial bookings** across 5 different movies (September 2025)
- **Booking statuses**: BOOKED and CANCELLED (simplified for clarity)
- **Various ticket prices** ($10-$25) and quantities (1-4 tickets)
- **Time-stamped transactions** with automatic created_at/updated_at tracking
- **Realistic movie data**: Popular movies with different price points

## 🔄 CDC Processing Logic

### Stream Processing
- **Automatic Capture**: Streams automatically detect all changes to source table
- **Metadata Addition**: Adds `METADATA$ACTION` and `METADATA$ISUPDATE` columns
- **Raw Data Storage**: Complete change history preserved in CDC events table

### Task Automation (`consume_stream_task`)
- **Scheduled Execution**: Runs every minute to process new changes
- **Raw Stream Consumption**: Populates CDC events table with complete stream data
- **Metadata Preservation**: Maintains all original fields plus change metadata
- **Error Handling**: Built-in retry and error logging capabilities

### Dynamic Table Processing
- **Enhanced Filtered Table**: 2-minute refresh lag, consumes from CDC events
- **Derived Field Calculation**: Business logic applied during refresh
- **Data Quality Filtering**: Invalid records filtered out automatically
- **Analytics Table**: Downstream refresh, aggregates from filtered table

## 📈 Analytics Capabilities

### Enhanced Key Performance Indicators
- **Total Bookings**: Count of all valid booking transactions
- **Active Revenue**: Revenue from BOOKED status bookings
- **Lost Revenue**: Revenue from CANCELLED status bookings
- **Data Quality Score**: Percentage of valid bookings
- **Cancellation Rate**: Percentage of cancelled bookings

### Business Categorization Analytics
- **Status Categories**: ACTIVE vs INACTIVE booking analysis
- **Size Categories**: SINGLE, GROUP, LARGE_GROUP booking patterns
- **Price Categories**: BUDGET, STANDARD, PREMIUM revenue analysis
- **Change Tracking**: INSERT, UPDATE, DELETE operation metrics

### Movie Performance Metrics
- **Revenue Analysis**: Active revenue vs lost revenue by movie
- **Booking Volume**: Total bookings with validity checks
- **Category Breakdown**: Bookings by size and price categories
- **Change Metrics**: New bookings, status changes, deletions

### Time-based Analysis
- **Date Range Filtering**: Flexible date range selection
- **Booking Hour Analysis**: Peak booking times
- **Day of Week Patterns**: Weekly booking trends
- **Real-time Updates**: 2-minute refresh for current insights

## 🎯 Use Cases

### Business Intelligence
- **Revenue Optimization**: Identify high-performing movies and time slots
- **Customer Behavior**: Analyze booking patterns and preferences
- **Operational Efficiency**: Monitor cancellation rates and booking trends

### Real-time Monitoring
- **Live Dashboard**: Monitor booking activity in real-time
- **Alert Systems**: Set up notifications for unusual patterns
- **Performance Tracking**: Track key metrics as they change

### Data Quality
- **Change Tracking**: Complete audit trail of all data modifications
- **Data Lineage**: Track data flow from source to analytics
- **Compliance**: Maintain historical records for regulatory requirements

## 📊 Dashboard Features

### Essential Interactive Filters
- **Date Range Selection**: Default September 2025, flexible date range
- **Status Filtering**: BOOKED, CANCELLED, or All bookings
- **Movie Selection**: Individual movie analysis or All movies
- **Refresh Button**: Manual data refresh capability

### Core Visualizations
- **Revenue by Status**: Bar chart showing active vs lost revenue
- **Booking Distribution**: Pie chart of booking status breakdown
- **Movie Performance Table**: Detailed metrics by movie
- **Real-time Insights**: Live analytics from dynamic tables

### Export and Navigation
- **CSV Download**: Export filtered data with timestamp
- **Raw Data View**: Expandable section for detailed data inspection
- **Clean Interface**: Beginner-friendly design with essential features
- **Responsive Layout**: Optimized for different screen sizes

## 🚀 Key Project Improvements

### Enhanced Architecture
- **Simplified Status Model**: Only BOOKED and CANCELLED statuses for clarity
- **Derived Field Engine**: Automatic business categorization and data quality scoring
- **Raw Stream Preservation**: Complete change history maintained in CDC events table
- **2-Minute Refresh Cycle**: Balanced real-time processing with cost efficiency

### Business Logic Enhancements
- **Revenue Tracking**: Separate active revenue vs lost revenue analysis
- **Booking Categorization**: Size-based (SINGLE/GROUP/LARGE_GROUP) and price-based (BUDGET/STANDARD/PREMIUM) classifications
- **Data Quality Metrics**: Built-in validation and quality scoring
- **Change Tracking**: Comprehensive INSERT/UPDATE/DELETE operation monitoring

### Dashboard Simplification
- **Essential Features Only**: Focused on core analytics without overwhelming complexity
- **Date Range Filtering**: Flexible time-based analysis with September 2025 defaults
- **Clean Interface**: Beginner-friendly design with intuitive navigation
- **Export Capabilities**: CSV download with timestamp for external analysis

## 🔮 Future Enhancements

### Potential Improvements
- **Machine Learning**: Predictive analytics for booking patterns and cancellation prediction
- **Real-time Alerts**: Automated notifications for unusual booking patterns
- **Advanced Visualizations**: More sophisticated chart types and interactive dashboards
- **API Integration**: REST API for external system integration
- **Multi-tenant Support**: Support for multiple movie theaters or locations

### Technical Enhancements
- **Data Lake Integration**: Connect to external data sources for enriched analytics
- **Streaming Analytics**: Real-time stream processing for immediate insights
- **Advanced CDC**: More sophisticated change detection with business rule validation
- **Performance Monitoring**: Enhanced monitoring and alerting for system health

---

**🎬 Movie Booking Analytics - Enhanced CDC with Derived Fields & Simplified Dashboard**

Ref: https://growdataskills.com/  
**🔧 Built with:** Snowflake Streams, Tasks, Dynamic Tables, Streamlit, Python
